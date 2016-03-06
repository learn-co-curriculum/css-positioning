# CSS Positioning

## Overview 

In this lesson we will learn the position property and z-index property to place elements into unique locations or adjust if they scroll with our content or stay fixed in place. We will cover a fe scenarios where using positioning can help to achieve specific results.

## Objectives

1. Positioning relative elements.
2. Positioning absolute elements.
3. Positioning absolute elements within a relative parent.
4. Positioning fixed elements.
4. Using z-index to control overlap.

## ...

<iframe width="640" height="360" src="https://www.youtube.com/embed/videoseries?list=PLj148bJp5wiwdWSz1kgDmh2VY-litDAcZ" frameborder="0" allowfullscreen></iframe>

*Note: Slides for this lecture video are provided in the resources at the bottom of this lesson.*

### Special Positioning

Float positioning gives us the flexibility to make grid systems to accomodate most layouts. There are however situations where other positioning techniques can be called upon to do more specialized kinds of positioning. I think of these positioning techniques as super powers that are appropriate to use in certain situations. Let's say for exmaple you wanted to adjust a radio button element top drop just a few pixels lower relative to where it used to be, or perhaps you want to position certain elements in relationship to the entire browser window, or perhaps you want an element such as a nav bar to stay fixed in place even when we scroll. These are all good scenarios to use special positioning. We can use the `position` property to change an elements position value.

### Static

`position: static;`

All elements display staticly by default. We can then set their position property to something else to adjust their positioning.

### Relative

In some situations you may want nudge an element relative to where it used to be located. This is done using relative positioning

`position: relative;`

Once you set an element to relative positioning you can then provide it commands top, right, bottom, and left to nudge it in one director or another.

`top: 20px`

This will push down on the element 20 pixels from where it used to be.

`left: 20px` 

This will push the element to the left from where it used to be. We can give these commands positive or negative numbers in pixels, percents, or ems. Positive numbers will push in towards the center of the element and negative numbers will pull the element away in the opposite direction so,

`left: 20px` is the same as `right: -20px`.

One thing to note about relative positioning is that when we move an element with relative positioning a ghost occupies the space where it used to exist. This means that text and other content can still not take up the origin al space where relative elements used to be positioned even though they have been moved to a new position.

#### HTML

```html
<input type="radio" name="size" value="small"> small<br>
<input type="radio" name="size" value="medium"> medium<br>
<input type="radio" name="size" value="large"> large
```

#### CSS

```css
input[type="radio"] {
  position: relative;
  top: 5px;
  left: 2px;
}
```

### Absolute

You may also want to position an alement in relationship to the entire browser window. Let's say for example you want to have some icons that always appear to the top right of the browser window. We can do this using absolute positioning.

`position: absolute;`

Simmiliar to relative as soon as we specific this positioning we can apply top, left, bottom, and right properties. This is where the similarities stop however as with absolute positioning these properties refer to the distance from the edge of the browser window instead of relative to where the element used to be.

`top: 20px`

This means 20px from the top of the screen.

`right: 0`

This means zero pixels from the right edge of the screen.

It is worth noting when you set an element to relative positioning uhnless you have specified a height or width, it will collpase to the size of its content. Thus if we want our absolutely positioned icons to have a width wider than the icons we must set their width accordingly.

#### HTML

```html
<nav>...icons here...</nav>
<div class="wrapper">
  ...
</div>
```

#### CSS

```css
nav {
  width: 20px;
  position: absolute;
  top: 0;
  right: 0;
}
```

The code above would position the icons into the top right corner of the browser window.

### Absolute Within A Relative Parent

Let's say you were building a juke box (ui) user interface on your webpage and you made graphics for the play and pause buttons among others. It would be nice to create an element with the id of jukebox and position the buttons within it. positioning them in relationship to their jukebox parent. We can accomplish this by setting the parent `#jukebox` to `position: relative` and the buttons to `position: absolute`. Whenebver we put an absolutely positioned element within a relatively positioned parent, the top, left, bottom, and right values are all in relationship to the parent.

`top: 20px`

This would mean 20px from the top of the `#jukebox` parent.

`left: 100px`

This would mean 100px from the left of the `#jukebox` parent.

#### HTML

```html
<div id="jukebox">
  <button class="play">play</button>
  <button class="play">pause</button>
</div>
```

#### CSS

```css 
#jukebox {
  position: relative;
}

.play {
    position: absolue;
    top: 20px;
    left: 100px;
}

.pause {
    position: absolue;
    top: 20px;
    left: 120px;
}
```

### Fixed

Another situation where some special positioning might come in handy is if you want an element to stay glued in place even when you scroll. To accomplish this we can use fixed positioning.

`position: fixed`

Fixed positioning follows the same rules as absolute positioning, except that elements that are fixed will stay put even when you scroll in any direction. Let's say for instance you wanted to make a top navigation bar stay fixed in place and have content scroll underneath it.

#### HTML

```html
<nav>
  <a>...</a>
  <a>...</a>
</nav>
<div class="wrapper">
  ...
</div>
```

#### CSS

```css
nav {
  width: 100%;
  position: fixed;
  top: 0;
  z-index: 1;
}
```

Here we set the nav bar to be 100% of the screen width and to position itself always at the top edge of the screen. Z-index keeps it on top which we'll discuss next.

### Z-Index

The Z-Index property allows us to layer elements in front of or behind each other. You can compare it to the concepts of layers in photo editing software such as Photoshop or the z-axis in math or in 3D modeling. The higher the number we give the z-index, the closer to us (in front), the lower the number the farther (behind) an elemnt appears. The default z-index is zero.

`z-index: 1;`

This will set an element to be on top of any elements with unspecified or lower numbers of z-index.

#### HTML

```html
<div class="a"> a </div>
<div class="b"> b </div>
<div class="c"> c </div>
```

#### CSS

```css

div {
  width: 50px;
  height: 50px;
  background: rgba(255,0,0,.25);
}

.a {
  position: relative;
  top: 0;
  left: 0;
  z-index: 1;
}

.b {
  position: relative;
  top: -25px;
  left: 25px;
  z-index: 2;
}

.c {
  position: relative;
  top: -50px;
  left: 50px;
  z-index: 3;
}
```

The code above will overlap the three boxes with `c` being on top.

## Summary

- We can alter the positioning behavior of elements by setting its `position` property.
- After setting the position, we have access to `top`, `left`, `bottom`, and `right` properties.
- These commands on a relative element will position it relative to where it used to be.
- These commands on absolute element are in relationship to the entire browser window.
- We can trap absolute positoned elments within a parent by setting their parent to relative positioning.
- Fixed positioning allows us to set an element to be fixed in place even when we scroll the window.
- The `z-index` property allows us to place elements in front or behind each other. Higher numbers go in front and lower numbers behind.

## Resources

- [Presentation Slides](https://docs.google.com/presentation/d/1UTUWDczUiDZ6byuhyHv0L3zJXQjdlnZheZXhRVLOL3Q/edit?usp=sharing)
- [Positioning - Code Example](http://jsfiddle.net/flatiron_school/rgyPC/1/)
- [Z-index - Code Example](http://jsfiddle.net/flatiron_school/nWGts/)
- [MDN - CSS - Position](https://developer.mozilla.org/en-US/docs/Web/CSS/position)
- [MDN - CSS - Z-index](https://developer.mozilla.org/en-US/docs/Web/CSS/z-index)
- [Learn CSS Positioning in Ten Steps](http://www.barelyfitz.com/screencast/html-training/css/positioning/)
