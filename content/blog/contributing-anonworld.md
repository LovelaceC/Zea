---
title: Contributing on Anonworld
type: default
layout: page
---

Hey!

If I sent you this, it means you are now an anonworld instructor/contributor.
Thank you so much, this is such a huge project and it requires a lot of effort
and there are several people working on it, and all of them (and now you) are
completely necessary to keep the project alive!

This is a guide so you can see all the stuff you can add, I will try to keep
this updated as time passes and more things are added to anonworld. For now,
this is the index of this entry:

- [Courses](#courses)
  - [Adding a course](#adding-a-course)
  - [Adding lessons](#adding-lessons)
  - [Updating a course](#updating-a-course)
  - [Adding a category](#adding-a-category)
- [Gamification](#gamification)
  - [Points](#points-elite-points--reputation)
  - [Achievements](#achievements)
  - [Ranks](#ranks)
- [Forum](#forum)
  - [Adding a new forum](#adding-a-new-forum)
  - [Updating a forum](#updating-a-forum)
  - [Re-ordering forums](#re-ordering-forums)
- [Adding a blog entry](#adding-a-blog-entry)

## Courses

The most important part on Anonworld are the courses. You need to be a tutor in
order to create, modify or update a course.

### Adding a course

In order to create a course, hover "Tutor LMS Pro" on the left sidebar, and
select "Courses", there all the available courses are going to be listed. You
can click the button "Add New" in the top of the site to create a new course.

Once you click that button, you get a page like an average post editor (I have
the classic editor plugin on) but the difference is that it will have a lot of
options for you to set.

The first thing we are going to set is the course title, you can set it by
setting a value in the input bar with the tip "Add title" you can write there
normally. Please set a meaningful name, don't put anything like "Cracking" or
"Computer Stuff", if you want to create a - for example - anonymity course,
please use a name like "Learn to improve your anonymity" or something like that.

At the right side of the title bar, there are some boxes "Publish", "Course
Language", "Course Categories", "Tags", "Tutor Settings" and "Featured Image".
Let's first talk about these boxes.

In the Publish box you can publish or update the course (in case your are
modifying it). There you can set its visibility and even schedule when the
course is going to be published. When you are finished, if you want the course
to be publicly available immediately, you can click the "Publish" button (make
sure "Visibility" is set to "Public").

In the Course Language box you can choose what language the course is written
in. If it is in a language that is still not available in that list, you can
click "Add New Language" and set it a name (please always start with a capital
letter). If the course's language is English, please select English.

In "Course Categories" choose the category of the course you will create. If
there is not a category that describes good enough the course you will add,
please create a new one (and tell me to add it on the main page, please don't
try to modify the theme), don't create your category using the "Add New
Category" button as it will create a very incomplete category, down below
there's an entire section talking about creating a category, please refer to it.

Once you have choosen your category, in the Tags box, you can set the tags for
your course. As there are not hundreds of people creating courses and there's no
competitivity either, this is not that necessary, anyway, adding tags is always
a good practise (but it is not required).

In the Tutor Settings box you can set some flags to modify how the students of
your course will be able to interact with it. You can make the course Public,
that is, it won't be necessary to people for enrol in it to see its contents,
you can also disable the Q&A and disable the certificate given to the students
after completion of your course. Please, don't select any of those flags (the
only one you can select is "Disable Q&A" just in case you don't want to give
support to your course).

And finally, in the Featured image, you can set your course's thumbnail. You can
see images like
[this](https://anonworld.eu/wp-content/uploads/2021/05/hackingscratch_2x.png)
and [this](https://anonworld.eu/wp-content/uploads/2021/05/C-language_4x.png)
for reference.

Your thumbnail's dimensions MUST be huge. You can use
[this tool](https://www.aiseesoft.com/image-upscaler/) to make it bigger without
losing quality.

Now, let's keep going in the center of the page.

In the big textbox you can set there the description of your course, please make
it extensive yet readable. What do I mean with that? Explain - as detailed as
possible - what the course is going to be about, what the people that enrol in
are going to learn, how the course is going to be structured and so on. You can
use the "Add Media" button if you want to include images in your description. If
you want, you can do it.

In case you see a box called "Course Options" activate the "Featured" checkbox,
if you do not, please contact me and I will do it for you.

You can skip the Excerpt box, I don't know what that is lmao.

In Course Settings you can set the maximum of students (please leave it 0 so
everybody can enrol in that course) and select a difficulty level. there are 4
difficulty levels available that you can choose from:

- All Levels
- Beginner
- Intermediate
- Expert

If your course is available for everybody, for example, if it has both beginner
and advanced topics, you can select All Levels. If it is mainly aimed for
beginners, select "Beginner" and so on.

Let's ignore "Course Builder" for now, and let's go to "Additional Data".

In additional data you can set your course duration. Please set an approximate
of what you think your content is worth in time, for example, if the lessons are
short but the course is about a complex theme, include ONLY the time the
students will spend by completing all the lessons. **Note**: You can modify this
value later, so don't worry if you still are not sure.

In "Benefits of the course" Set what are the benefits of the course, what the
student is going to learn after completing it (_separate each "benefit" with a
newline_) for example, in my C course, it looks like:

```text
Understand the fundamentals of the C programming language.
Create your first C application.
Learn one of the most popular and widely used languages in the world.
Understand variables and different data types.
Understand the core language that most modern languages are based on.
Learn how to write high-quality code.
```

In "Requirements/Instructions" you can set the things that are required in order
for the student to be able to complete the course without any trouble, again,
the ones in my C course are:

```text
A computer running Microsoft Windows, Linux or a BSD operating system
At least 4 GB of ram is recommended.
No programming experience is required, all concepts will be taught in this course.
```

And the contents of "Target Audience" and "Materials Included" is optional.

If your course is going to be text-based, that is, is going to be only (or
mainly) text, don't select anything in the Video box.

### Adding lessons

Once you have created a course you can go ahead and create sections and lessons.
What's the difference between them? Let me show you with an image:

![](/img/blog/sections.png)

As you can see in that image (Taken from the course "Hacking from Scratch") The
following are sections:

- Introduction
- Hacking Lab
- Introduction to Linux
- Network Hacking - Introduction

And both "Introduction to Hacking" and "What is hacking, a hacker and why should
I learn it?" are lessons.

That's what we are going to learn to create in this section.

The first thing we are going to do is to create a section, as there cannot be
lessons without sections. So, let's go a head. Open the course's edit page and
go to the "Course Builder" box.

If you are going to create a section, click the button "Add New Topic" and two
more input boxes will appear: "Topic Name" and "Topic Summary".

In "Topic Name" you set the section's name, for example, using the previous
image as reference it would be "Introduction" and in "Topic Summary" you'd set
the section description, using this same section in the previous image, that
section's description was: "An introduction to this course, how it is going to
work and a little bit of theory".

When you are finished setting those values, you can click "Add Topic" now and it
will be added.

Once we have a section created, we can create a lesson now. In order to do that,
first, determine in which section you want to create your lesson in. Click that
section's title and click the blue button at the end of it.

You can see there are two blue buttons "Lesson" and "Quiz", you can use each one
of them to create either a Lesson or a Quiz. In this case, we want to create a
lesson, so we are going to click the Lesson button.

A pop-up will appear, with new more data for us to set :3

The first thing we are going to set is the lesson name, please set a meaningful
name too, don't do something like "A lesson", "Another lesson", "Third lesson"
please make it something like "What is...?" "How to...?" and stuff like that.

In the big textbox you can set there the lesson content, you can click the "Add
Media" button to add images, as if it were an average wordpress post.

Once you are finished with that, please don't click "Update Lesson" yet, we need
to add more stuff yet. Scroll down a little and you will see "Featured Image",
there, click "Add Featured Image" and select the course image, please don't
upload it again, that's just a waste of storage, just look for it in the media
explorer, and that's it. You can now click "Add Lesson" for add it to your
course, take in account that it is not necessary to click the course's "Update"
button.

### Updating a course

Updating an already existing course is very easy. All you have to do is to go to
the "Courses" button under the "Tutor LMS Pro" menu, look for your course, click
its title, and you can modify it there.

It's the exact same thing as creating a course, some button's text might change.
But with a little of common sense you can do the same things.

### Adding a category

In order to create a category, click the "Categories" menu under the "Tutor LMS
Pro" menu, there you will see an "Add New Category" section, there you can set
the data to create your section.

In Name, you will set the name of your category, for example, "Low Level
Programming" and in slug, set the same name slugified, for example, "Low Level
Programming" would be "low-level-programming" now.

If your category is a sub-category, please select the parent category in the
next list.

Then, set a description about your category, it doesn't have to be very
detailed, for example, for "Low Level Programming" a good description would be
"Learn Low Level Programming, how things actually work under the hood, create
performance-critic programs and much more".

Finally, set an image, as with the courses thumbnail, its dimensions MUST be
very big check
[this](https://anonworld.eu/wp-content/uploads/2021/05/kali-blue-header.jpg) or
[this](https://anonworld.eu/wp-content/uploads/2021/05/website-hacking-with-ngrok_6x.jpg)
for reference.

## Gamification

TODO: This

### Points (Elite points / Reputation)

TODO: This

### Achievements

TODO: This

### Ranks

TODO: This

## Forum

TODO: This

### Adding a new forum

TODO: This

### Updating a forum

TODO: This

### Re-ordering forums

TODO: This

## Adding a blog entry

TODO: This
