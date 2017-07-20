# Spooky Framework

![SPOOKY](http://i.imgur.com/Ut23RfP.png)

Spooky Framework is a lightweight, modular, front-end development framework targeted at animation-driven websites. It is tailored to work with [GSAP](https://greensock.com/gsap) and can be easily used with [PIXI.js](http://www.pixijs.com/) and [three.js](https://threejs.org/).

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

### No Virtual DOM Overhead

Popular frameworks like Vue and React rely heavily on using virtual DOM, which works great for building data-driven websites and applications, since only some parts of a web-app need to be updated when the data changes.

Animation libraries like GSAP work by manipulating the DOM that is already in the document, so the virtual DOM still needs to be appended to the document and kept in the same state so that GSAP can manipulate and keep track individual DOM elements.

Spooky Framework works by building out individual DOM components without using the virtual DOM overhead. The Framework still keeps performance in mind by creating the DOM structure 'off-screen' and only appending it to the documnet when all the child elements are already created, so that there is only one append call with all the children elements already in it.

When building out the HTML markup (which is conveniently placed inside the JS file) the reference to DOM elements is available right away, even through it is not added to the document yet. This allows you to easily manipulate DOM elements and create references to its children before they are even added to the document.

### Code Organization

Each UI component and section is organized by the Spooky Generator into it's own folder with 2 files, a JS file and a SCSS style. The markup is placed inside the JS file using string literals (powered by [yo-yo](https://github.com/maxogden/yo-yo)) which makes it really easy to see all available DOM elements within the JS file.

Here's an example of the JS file for a customizable Ghost button with mouse-over/mouse-out animation (using Javascript)

```javascript
require('./Button.scss');
const SpookyEl = require('spooky-element');
var yo = require('yo-yo');

class GhostButton extends SpookyEl {

  constructor(data={}){
    super();
    // Set defaults
    data = Object.assign({}, {
      label: 'SUBMIT',
      backgroundColor: '#000',
      color: "#000",
      hoverColor: '#fff'
    }, data);

    // Create the DOM, inline
    this.view = yo`
    <div class="ui-ghost-button" style="color: ${data.color}; border-color: ${data.color};">
      <div class="button-bg" style="background-color: ${data.color}"></div>
      <div class="label">${data.label}</div>
    </div>`;

    this.label = this.find('.label');
    this.bg = this.find('.button-bg');
    // Initially hide the background
    gsap.set(this.bg, {autoAlpha:0});

    this.on('mouseenter', (e) => {
      gsap.to(this.bg, 0.3, {autoAlpha:1, ease:Sine.easeOut});
      gsap.to(this, 0.3, {bordeColor:data.backgroundColor, ease:Sine.easeOut});
      gsap.to(this.label, 0.3 {color:data.hoverColor, ease:Sine.easeOut});
    });
    this.on('mouseleave', (e) => {
      gsap.to(this.bg, 0.3 {autoAlpha:0, ease:Sine.easeOut});
      gsap.to(this, 0.3, {bordeColor:data.color, ease:Sine.easeOut});
      gsap.to(this.label, 0.3 {color:data.color, ease:Sine.easeOut});
    });

  }

}
export default GhostButton;
```

And the SCSS file

```scss
.ui-button {

  padding: 10px 15px;
  min-width: 200px;
  position: relative;
  cursor: pointer;
  display: inline-flex;
  align-items: center;
  justify-content: center;
  border: 1px solid #fff;

  .button-bg {
    position: absolute;
    width: 100%;
    height: 100%;
    z-index: 0;
  }

  .label {
    position: relative;
    z-index: 1;
    text-transform: uppercase;
  }

}
```


