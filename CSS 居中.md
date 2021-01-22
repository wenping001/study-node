# CSS 居中



## 水平居中

> 是否是 内联元素（inline） 或是 inline-* elements （text of links）

```css
.center-chidren{
    text-align:center;
}
```

适用于 inline, inline-block, inline-table, inline-flex, 等.

> 块元素

```css
.center-me{
    margin:0 auto;
}
```

> 多个块元素

如果有多个块元素需要在一行水平居中，最好是将他们设为为不同的display类型。

* inline-block and flexbox

  ```html
  <main class="inline-block-center">
    <div>
      I'm an element that is block-like with my siblings and we're centered in a row.
    </div>
    <div>
      I'm an element that is block-like with my siblings and we're centered in a row. I have more content in me than my siblings do.
    </div>
    <div>
      I'm an element that is block-like with my siblings and we're centered in a row.
    </div>
  </main>
  
  <main class="flex-center">
    <div>
      I'm an element that is block-like with my siblings and we're centered in a row.
    </div>
    <div>
      I'm an element that is block-like with my siblings and we're centered in a row. I have more content in me than my siblings do.
    </div>
    <div>
      I'm an element that is block-like with my siblings and we're centered in a row.
    </div>
  </main>
  ```

  ```css
  body {
    background: #f06d06;
    font-size: 80%;
  }
  
  main {
    background: white;
    margin: 20px 0;
    padding: 10px;
  }
  
  main div {
    background: black;
    color: white;
    padding: 15px;
    max-width: 125px;
    margin: 5px;
  }
  
  .inline-block-center {
    text-align: center;
  }
  .inline-block-center div {
    display: inline-block;
    text-align: left;
  }
  
  .flex-center {
    display: flex;
    justify-content: center;
  }
  ```

  

  ![capture_20210120130815796](D:\HONOR Magic-link\Screenshot\capture_20210120130815796.bmp)

## 垂直居中

> 内联元素  inline   inline-* 

* 单行

  ```css
  .link{
      padding-top:30px;
      padding-bottom:30px;
  }
  ```

  

* 多行

  ```css
  .flex-center-vertically {
    display: flex;
    justify-content: center;
    flex-direction: column;
    height: 400px;
  }
  ```

  

>块元素

* known height
* unknown height

* element stretches the height of the container
* use flexbox

## 水平垂直居中

> 固定宽高

```css
.parent {
  position: relative;
}

.child {
  width: 300px;
  height: 100px;
  padding: 20px;

  position: absolute;
  top: 50%;
  left: 50%;

  margin: -70px 0 0 -170px;
}
```



> 未知高度长度

```css
.parent {
  position: relative;
}
.child {
  position: absolute;
  top: 50%;
  left: 50%;
  transform: translate(-50%, -50%);
}
```



> use flexbox

```css
.parent {
  display: flex;
  justify-content: center;
  align-items: center;
}
```



> use grid

```css
body, html {
  height: 100%;
  display: grid;
}
span { /* thing to center */
  margin: auto;
}
```





# Flexbox 



> Basics & Terminology

![A diagram explaining flexbox terminology. The size across the main axis of flexbox is called the main size, the other direction is the cross size. Those sizes have a main start, main end, cross start, and cross end.](https://css-tricks.com/wp-content/uploads/2018/11/00-basic-terminology.svg)

Items will be laid out following either the `main axis` (from `main-start` to `main-end`) or the cross axis (from `cross-start` to `cross-end`).

- **main axis** – The main axis of a flex container is the primary axis along which flex items are laid out. Beware, it is not necessarily horizontal; it depends on the `flex-direction` property (see below).
- **main-start | main-end** – The flex items are placed within the container starting from main-start and going to main-end.
- **main size** – A flex item’s width or height, whichever is in the main dimension, is the item’s main size. The flex item’s main size property is either the ‘width’ or ‘height’ property, whichever is in the main dimension.
- **cross axis** – The axis perpendicular to the main axis is called the cross axis. Its direction depends on the main axis direction.
- **cross-start | cross-end** – Flex lines are filled with items and placed into the container starting on the cross-start side of the flex container and going toward the cross-end side.
- **cross size** – The width or height of a flex item, whichever is in the cross dimension, is the item’s cross size. The cross size property is whichever of ‘width’ or ‘height’ that is in the cross dimension.

## 父元素属性 （flex container）

* display

  定义一个 flex 容器

  ```css
  .container{
      display:flex;  
  }
  ```

  

* flex-direction

  ![the four possible values of flex-direction being shown: top to bottom, bottom to top, right to left, and left to right](https://css-tricks.com/wp-content/uploads/2018/10/flex-direction.svg)

  ```css
  .container {
    flex-direction: row | row-reverse | column | column-reverse;
  }
  ```

  

* flex-wrap

  ![two rows of boxes, the first wrapping down onto the second](https://css-tricks.com/wp-content/uploads/2018/10/flex-wrap.svg)

  ```css
  .container{
      flex-wrap: nowrap | wrap | wrap-reverse;
  }
  ```

  - `nowrap` (default): all flex items will be on one line
  - `wrap`: flex items will wrap onto multiple lines, from top to bottom.
  - `wrap-reverse`: flex items will wrap onto multiple lines from bottom to top.

* flex-flow

  This is a shorthand for the `flex-direction` and `flex-wrap` properties, which together define the flex container’s main and cross axes. The default value is `row nowrap`

  ```css
  .container {
    flex-flow: column wrap;
  }
  ```

* justify-content

  ![flex items within a flex container demonstrating the different spacing options](https://css-tricks.com/wp-content/uploads/2018/10/justify-content.svg)

  ```css
  .container {
    justify-content: flex-start | flex-end | center | space-between | space-around | space-evenly | start | end | left | right ... + safe | unsafe;
  }
  ```

* align-items

  ![demonstration of differnet alignment options, like all boxes stuck to the top of a flex parent, the bottom, stretched out, or along a baseline](https://css-tricks.com/wp-content/uploads/2018/10/align-items.svg)

  ```css
  .container {
    align-items: stretch | flex-start | flex-end | center | baseline | first baseline | last baseline | start | end | self-start | self-end + ... safe | unsafe;
  }
  ```

  

* align-content

  ![examples of the align-content property where a group of items cluster at the top or bottom, or stretch out to fill the space, or have spacing.](https://css-tricks.com/wp-content/uploads/2018/10/align-content.svg)

  ```css
  .container {
    align-content: flex-start | flex-end | center | space-between | space-around | space-evenly | stretch | start | end | baseline | first baseline | last baseline + ... safe | unsafe;
  }
  ```

  

## 子元素属性（flex items）

* order

  ![Diagram showing flexbox order. A container with the items being 1 1 1 2 3, -1 1 2 5, and 2 2 99.](https://css-tricks.com/wp-content/uploads/2018/10/order.svg)

  ```css
  .item {
    order: 5; /* default is 0 */
  }
  ```

  

* flex-grow

  ![two rows of items, the first has all equally-sized items with equal flex-grow numbers, the second with the center item at twice the width because its value is 2 instead of 1.](https://css-tricks.com/wp-content/uploads/2018/10/flex-grow.svg)

  ```css
  .item {
    flex-grow: 4; /* default 0 */
  }
  ```

  

# Grid

## Important Terminology

**Grid Container**

The element on which `display: grid` is applied. It’s the direct parent of all the grid items. In this example `container` is the grid container.

```css
<div class="container">
  <div class="item item-1"> </div>
  <div class="item item-2"> </div>
  <div class="item item-3"> </div>
</div>
```

**Grid Line**

The dividing lines that make up the structure of the grid. They can be either vertical (“column grid lines”) or horizontal (“row grid lines”) and reside on either side of a row or column. Here the yellow line is an example of a column grid line.

<img src="https://css-tricks.com/wp-content/uploads/2018/11/terms-grid-line.svg" alt="img" style="zoom:50%;" />

**Grid Track**

The space between two adjacent grid lines. You can think of them like the columns or rows of the grid. Here’s the grid track between the second and third row grid lines.

<img src="https://css-tricks.com/wp-content/uploads/2018/11/terms-grid-track.svg" alt="img" style="zoom:50%;" />

**Grid Area**

![img](https://css-tricks.com/wp-content/uploads/2018/11/terms-grid-area.svg)

**Grid Item**

The children (i.e. *direct* descendants) of the grid container. Here the `item` elements are grid items, but `sub-item` isn’t.

```css
<div class="container">
  <div class="item"> </div>
  <div class="item">
    <p class="sub-item"> </p>
  </div>
  <div class="item"> </div>
</div>
```

**Grid Cell**

The space between two adjacent row and two adjacent column grid lines. It’s a single “unit” of the grid. Here’s the grid cell between row grid lines 1 and 2, and column grid lines 2 and 3.

![img](https://css-tricks.com/wp-content/uploads/2018/11/terms-grid-cell.svg)

## Grid Properties Table of Contents

**display**

Defines the element as a grid container and establishes a new grid formatting context for its contents.

```css
.container{
    display: grid | inline-grid;
}
```

**grid-template-columns** 
 **grid-template-rows**

