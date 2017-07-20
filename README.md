# Spooky Framework

![SPOOKY](http://i.imgur.com/Ut23RfP.png)

Spooky Framework is a lightweight, front-end development framework targeted at animation-driven websites. It is tailored to work with [GSAP](https://greensock.com/gsap) and can be easily used with [PIXI.js](http://www.pixijs.com/) and [three.js](https://threejs.org/).

The name Spooky came from the initial reaction developers and producers had when they saw how quick and easy it was to build heavily-animated websites. It is spooky that something like this didn't exist already.

## :ghost: Goals

The framework has been created with the following goals in mind:

- Easy To Understand (Mostly vanilla Javascript with )
- Fast Performace
- Quick to Develop With
- Works Well With Other Libraries (GSAP, PIXI, ThreeJS, Vue, React)
- Helps Organize Code and Generate Boilerplate Code

## In The Wild

Spooky Framework has been battle-tested on the following award-winning websites:

- [Sons of Gallipoli](http://sonsofgallipoli.com/)
- [Tame the Dragon](http://www.tamethedragon.com/)
- [Mixtape of You](http://mixtapeofyou.com/)
- [Camp Jefferson](http://campjefferson.com/)
- [Reflektor Digital](https://reflektor.digital/)
- [Spy Films](http://spyfilms.com/)

## Stucture

Spooky Framework is put together using a number of different componenents, which can be used independently.

- [spooky-element](https://github.com/maxtherocket/spooky-element) For creating, manipulating and organizing DOM elements.
- [spooky-router](https://github.com/maxtherocket/spooky-router) For managing web site sections through routes.
- [generator-spooky](https://github.com/maxtherocket/generator-spooky) A Yeoman generator to help speed up development and organize code. Generates boilerplate code for the initial project structure, sections and individual UI components. Which makes development extremenly fast :rocket:

## Why?

Popular frameworks like Vue and React rely heavily on using virtual DOM, which works great for building data-driven websites and applications, since only some parts of a web-app need to be updated when the data changes. Animation libraries like GSAP work by manipulating the DOM that is already in the document, so the virtual DOM still needs to be appended to the document and kept in the same state so that GSAP can manipulate and keep track individual DOM elements.

Spooky Framework works by building out individual DOM components without using the virtual DOM overhead. The Framework still keeps performance in mind by creating the DOM structure 'off-screen' and only appending it to the documnet when all the child elements are already created, so that there is only one append call with all the children elements already in it.






