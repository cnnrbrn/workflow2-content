# Lesson 2 - An introduction to Jest

## Introduction

<a href="https://jestjs.io/" target="_blank">Jest</a> is a tool that allows us to test JavaScript code.

In this brief introduction, we'll install Jest and use it to test the return value of a function.

The value of testing lies in being certain that changes you make to your code won't break other parts of your program.

You will probably come across the term TDD or Test-Driven Development.

This method of development involves writing tests before you write your actual code. At first the test(s) will fail, and as you implement your code the test(s) will pass.

TDD won't be covered in this course.

---

## A first Jest test

<iframe src="https://player.vimeo.com/video/506827581" height="500" frameborder="0" allow="autoplay; fullscreen; picture-in-picture" allowfullscreen></iframe>

<a href="https://vimeo.com/506827581/8202fd20a8" target="_blank">Watch on Vimeo</a>

<a href="https://github.com/NoroffFEU/introduction-to-jest" target="_blank">Code from the video</a>

---

## Matchers

Jest users matchers to test for values.

In the video above we used the `toBe` matcher.

If we wanted to test for an object value we would use the `toEqual` matcher.

Consult the <a href="https://jestjs.io/docs/en/using-matchers" target="_blank">official docs</a> when writing your tests to find an appropriate matcher.

<!-- ---

[Go to lesson 3](3)

--- -->
