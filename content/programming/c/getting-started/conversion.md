---
title: Integer and Float Conversions
type: default
layout: page
child: Programming
---

In order to effectively develop C programs, it will be necessary to understand
the rules that are used for the implicit conversion of floating point and
integer values in C. These are mentioned below. Note them carefully:

- An arithmetic operation between an integer and an integer ALWAYS yields an
integer result.
- An operation between a real and a real always yields a real result.
- An operation betwen an integer and real always yields a real result. In this
operation the integer is first promoted to a real and then the operation is
performed. Hence, the result is real.
