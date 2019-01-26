---
title: Interactive Javascript Animations with Trigonometry
date: '2019-01-23'
---

## Math - Mental Abuse To Humans

Back in my school days, this is how I used to feel about math. Beyond basic arithmetic I couldn't see when I'd ever need to use the subjects they taught in real life, and I got by like that, even into my first several months of programming, as you don't tend to use much linear algebra or trigonometry when creating user interfaces in React.

As I started to take on creative coding projects and 3D development though, I soon changed my tune and started to learn to love math. The more I brush up on my fundamentals the more fun I tend to have when coding interactive experiences and so I've decided to start sharing what I learn to reinforce it and act as a reference for future me who's bound to forget stuff.

In this post I'm sharing some simple trigonometry techniques that have proved useful on several occasions. To do so we will create a little demo of an eye-ball that looks at your cursor as you move it around the screen.


## Canvas Set-up

We start with a simple canvas set-up with a draw loop that gets fired on a request animation frame and a handle resize listener to keep the demo responsive.

Then inside the draw loop we define two objects, one for the eye and one for it's pupil. These both have an x and y coordinate and a radius.

``` javascript
const eye = {
  x: width / 2,
  y: height / 2,
  radius: 50
};

const pupil = {
  x: eye.x,
  y: eye.y,
  radius: eye.radius / 2
};
```

For the eyes coordinates I've used the center of the screen and a radius of 50. The pupil uses the same coordinates as the eye (for now) and half the eyes radius.

Try playing with the pupils coordinates a little by adding 20px to the pupils x coordinate and 15px to its y.

``` javascript
const pupil = {
  x: eye.x + 20,
  y: eye.y + 10,
  radius: eye.radius / 2
};
```

See how it's looking down to the right now? 

It's by adding and subtracting small amounts to the pupils x and y coordinates that we can control the direction the eye appears to look.

But how do we know what numbers to use?

https://codepen.io/adammarcwilliams/pen/mvdQyG


## Rolling the Eyes - Sine & Cosine

Turns out we can use a couple of trigonometric functions called sine and cosine to work out what numbers we'll need to roll our eyes around in a circle.

These functions take an angle and return a value between -1 to 1 and when used together can plot a point around a unit circle.

[![Sine Cosine Relationship](./Circle_cos_sin.gif)](https://commons.wikimedia.org/wiki/File:Circle_cos_sin.gif)

This is a common pattern you'll use whenever you want to rotate anything in a circle around a center point and it looks like this.

``` javascript
x = center.x + Math.cos(angle) * offset
y = center.y + Math.sin(angle) * offset
```

Given the angle that's passed in it will give you the position needed to plot that angle around a circle using the offset to determine how far away from the center it should be.



A couple of things to note is that the angle you pass is in radians, not degrees. This is easy to convert:

```javascript
radians = degrees * Math.PI / 180
degrees = radians * 180 / Math.PI
```

Also the circle starts at 3 o'clock not the top. In canvas it travels clockwise as you may expect but in math traditionally and in other libraries it will travel anti-clockwise.

Lastly it's common to see angles stored using the name `theta` which is what I've done in our demo.

https://codepen.io/adammarcwilliams/pen/jdOeZJ

## Follow the Cursor - Solving for Triangles

Lorem ipsum dolor sit amet, consectetur adipiscing elit, sed do eiusmod tempor incididunt ut labore et dolore magna aliqua. Ut enim ad minim veniam, quis nostrud exercitation ullamco laboris nisi ut aliquip ex ea commodo consequat. Duis aute irure dolor in reprehenderit in voluptate velit esse cillum dolore eu fugiat nulla pariatur. Excepteur sint occaecat cupidatat non proident, sunt in culpa qui officia deserunt mollit anim id est laborum.

https://codepen.io/adammarcwilliams/pen/yZLQOe

## Bonus Trigonometry

Lorem ipsum dolor sit amet, consectetur adipiscing elit, sed do eiusmod tempor incididunt ut labore et dolore magna aliqua. Ut enim ad minim veniam, quis nostrud exercitation ullamco laboris nisi ut aliquip ex ea commodo consequat. Duis aute irure dolor in reprehenderit in voluptate velit esse cillum dolore eu fugiat nulla pariatur. Excepteur sint occaecat cupidatat non proident, sunt in culpa qui officia deserunt mollit anim id est laborum.

