---
title: I/O Devices - Operating Systems - Computer Science
type: default
layout: page
child: Computer Science
fold: Operating Systems
---

![](/img/computer-science/os/components.png)

The CPU and memory are not the only resources that the operating system must
manage. I/O devices also interact heavily with the operating system. As we saw
in the above image, I/O devices generally consist of two parts: a controller and
the device itself. The controller is a chip or a set of chips that physically
controls the device. It accepts commands from the operating system, for example,
to read data from the device, and carries them out.

In many cases, the actual control of the device is complicated and detailed, so
it is the job of the controller to present a simpler (but still very complex)
interface to the operating system. For example, a disk controller might accept a
command to read sector 11.206 from disk 2. The controller then has to convert
this linear sector number to a cylinder, sector and head. This conversion might
be complicated by the fact that outer cylinders have more sectors than inner
ones and that some bad sectors have been remapped onto other ones. Then the
controller has to determine which cylinder the disk arm is on and give it a
command to move in or out the requisite number of cylinders. It has to wait
until the proper sector has rotated under the head and then start reading and
storing the bits as they come off the drive, removing the preamble and computing
the checksum. Finally, it has to assemble the incoming bits into words and store
them in memory. To do all this work, controllers often contain small embedded
computers that are programmed to do their work.

The other piece is the actual device itself. Devices have fairly simple
interfaces, both because they cannot do much and to make them standard. The
latter is needed so that any SATA disk controller can handle any SATA disk, for
example. **SATA** stands for **Serial ATA** and **ATA** in turns stands for **AT
Attachment**. In case you are curious about what AT stands for, this was IBM's
second generation "_Personal Computer Advanced Technology_" built around the
then-extremely-potent 6-MHz 80286 processor that the company introduced in 1984.
What we learn from this is that the computer industry has a habit of
continuously enhancing existing acronyms with new prefixes and suffixes. We also
learned that an adjective like "_advanced_" should be used with great are, or
you will look silly fourty years down the line.

SATA is currently the standard type of disk on many computers. Since the actual
device interface is hidden behind the controller, all that the operating system
sees is the interface to the controller, which might be quite different from the
interface to the device.

Because each type of controller is different, different software is needed to
control each one. The software that talks to a controller, giving it commands
and accepting responses, is called a **device driver**. Each controller
manufacturer has to supply a driver for each operating system it supports. Thus
a scanner might come with drivers for OS X, Windows 8, Windows 10 and Linux, for
example.

To be used, the driver has to be put into the operating system so it can run in
kernel mode. Drivers can actually run outside the kernel, and operating systems
like Linux and Windows nowadays do offer some support for doing so. The vast
majority of the drivers still run below the kernel boundary. Only very few
systems, such as MINIX 3, run all drivers in userspace. Drivers in userspace
must be allowed to access the device in a controller way, which is not
straightforward.

There are three ways the driver can be put into the kernel. The first way is to
relink the kernel with the new driver and then reboot the system. Many older
UNIX systems work like this. The second way is to make an entry in an operating
system file telling it that it needs the driver and then reboot the system. At
boot-time, the operating system goes and finds the drivers it needs and loads
them. Windows works this way. The third way is for the operating system to be
able toa ccept new drivers while running and install them on the fly without the
need to reboot. This way used to be rare but is becoming much more common now.
Hot-pluggable devices, such as USB and IEEE 1394 devices (discussed below),
always need dynamically loaded drivers.

Every controller has a small number of registers that are used to communicate
with it. For example, a minimal disk controller might have registers for
specifying the disk address, memory address, sector count and direction (read or
write). To activate the controller, the driver gets a command from the operating
system, then translates it into the appropriate values to write into the device
registers. The collection of all the devices registers form the **I/O port
space**, a subject we will come back to later on.

On some computers, the device registers are mapped into the operating system's
address space (the addresses it can use), so they can be read and written like
ordinary memory words. On such computers, no special I/O instructions are
required and user programs can be kept away from the hardware by not putting
these memory addresses within their reach (e.g., by using base and limit
registers). On other computers, the device registers are put in a special I/O
port space, with each register having a port address. On these machines, special
IN and OUT instructions are available in kernel mode to allow drivers to read
and write the registers. The former scheme eliminates the need for special I/O
nstructions but uses up some of the address space. The latter uses no address
space but requires special instructions. Both systems are widely used.

Input and output can be done in three different ways. In the simples method, a
program issues a system call, which the kernel then translates into a procedure
call to the appropriate driver. The driver then starts the I/O and sits in a
tight loop continously polling the device to see if it is done (usually there is
some bit that indicates that the device is still busy). When the I/O has
completed, the driver puts the data (if any) where they needed and returns. The
operating system then returns control to the caller. This method is called
**busy waiting** and has the disadvantage of tying up the CPU polling the device
until it is finished.

The second method is for the driver to start the device and ask it to give an
interrupt when it is finished. At that point the driver returns. The operating
system then blocks the caller if need be and looks for other work to do. When
the controller detects the end of the transfer, it generates and **interrupt**
to signal completion.

Interrupts are very important in operating systems, so let's examine the idea
more closely.

![](/img/computer-science/os/io.png)

In the above image (a) we see a three-step process for I/O. In step 1, the
driver tells the controller what to do by writing into its device registers. The
controller then starts the device. When the controller has finished reading or
writing the number of bytes it has been told to transfer, it signals the
interrupt controller chip using certain bus lines in step 2. If the interrupt is
ready to accept the interrupt (which it might not be if it is busy handling a
higher-priority one), it asserts a pin on the CPU chip telling it, in step 3. In
step 4, the interrupt controllerputs the number of the device on the bus so the
CPU can read it and know which device has just finished (many devices might be
running at the same time).

Once the CPU has decided to take the interrupt, the program counter and PSW are
typically then pushed onto the current stack and the CPU switched into kernel
mode. The device number might be used as an index into part of memory to find
the address of the interrupt handler for this device. This part of memory is
called **interrupt vector**. Once the interrupt handler (part of the driver for
the interrupting device) has started, it removes the stacked program counter and
PSW and saves them, then queries the device to learn its status. When the
handler is all finished, it returns to the previously running user program to
the first instruction that was not yet executed. These steps are shown in (b).

The third method for doing I/O makes the use of special hardware: a **DMA**
(**Direct Memory Access**) chip that can control the flow of bits between memory
and some controller without constant CPU intervention. The CPU sets up the DMA
chip, telling it how many bytes to transfer, the device and memory addresses
involved, and the direction, and lets it go. When the DMA chip is done, it
causes an interrupt, which is handled as described above. DMA and I/O hardware
in general will be discussed in more detail later.

Interrupts can (and often do) happen at highly inconvenient moments, for
example, while another interrupt handler is running. For this reason, the CPU
has a way to disable interrupts and then reenable them later. While interrupts
are disabled, any devices that finish continue to assert their interrupt
signals, but the CPU is not interrupted until interrupts are enabled again. If
multiple devices finish while interrupts are disabled, the interrupt controller
decides which one to let through first, usually based on static priorities
assigned to each device. The highest-priority device wins and gets to be
serviced first. The others must wait.
