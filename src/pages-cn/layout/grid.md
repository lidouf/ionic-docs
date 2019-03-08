---
initialTab: 'preview'
inlineHtmlPreviews: true
previousText: 'Structure'
previousUrl: '/docs/layout/structure'
nextText: 'CSS Utilities'
nextUrl: '/docs/layout/css-utilities'
contributors:
  - brandyscarney
---

<link rel="stylesheet" href="https://unpkg.com/@ionic/core/css/padding.css">
<link rel="stylesheet" href="https://unpkg.com/@ionic/core/css/float-elements.css">
<link rel="stylesheet" href="https://unpkg.com/@ionic/core/css/text-alignment.css">
<link rel="stylesheet" href="https://unpkg.com/@ionic/core/css/text-transformation.css">
<link rel="stylesheet" href="https://unpkg.com/@ionic/core/css/flex-utils.css">

# 响应式栅格

栅格是一个强大的、移动优先的flexbox系统，用来构建自定义布局。它由三个基本单位组成--[网格](/docs/api/grid), [行](/docs/api/row)和[列](/docs/api/col)。列会扩展去填充它们的行，并且会调整大小去适应额外的列。它基于12列布局，根据不同的屏幕尺寸会有不同的breakpoint。列的数量可以使用CSS进行修改。


## 它是如何工作的

```html
<ion-grid>
  <ion-row>
    <ion-col>
      <div>
        1 of 3
      </div>
    </ion-col>
    <ion-col>
      <div>
        2 of 3
      </div>
    </ion-col>
    <ion-col>
      <div>
        3 of 3
      </div>
    </ion-col>
  </ion-row>
</ion-grid>
```

- 网格就像盛装所有行和列的一个容器。网格会占有所有容器的完整宽度，但如果添加了`fixed`属性则会指定每个屏幕的大小，具体参见下方的[网格大小](#grid-size)。
- 行是列的水平分组，它能够恰当的安排各列（在水平上）。
- 内容应该放在列内，仅有列可能才是行最直接的子孙。
- `size-{breakpoint}`属性表示使用每行默认的12列里面的几列。因此，`size="4"`可以加在列上面表示占有网格的1/3，或者12列中的4列。
- 如果列没有标明大小则会自动等宽。例如，四个`size-sm`实例表示每个实例自动获得small breakpoint及以上25%的宽度。
- 列宽按百分比设置，所以它们通常是流式的(fluid)，并且大小是相对于它们的父元素而言的。
- 各列之间有间隔，但是，可以移除网格和列之间的间隔，通过在在网格添加`no-padding`属性实现。
- 有五个网格层级，每个表示一种响应式breakpoint：all breakpoints (extra small), small, medium, large, and extra large。
- 网格层级基于最小宽度表示，意思是大于等于该尺寸的使用这个层级。(例如，`size-sm="4"`生效的是small, medium, large, and extra large设备)。
- 网格可以通过CSS变量方便进行定制。参见[定制网格](#customizing-the-grid)。


## 网格大小

网格默认占用100%宽度。要基于屏幕大小设置指定的网格宽度，添加`fixed`属性。每个breakpoint的网格宽度定义在`--ion-grid-width-{breakpoint}` CSS变量之中。参见[定制网格](#customizing-the-grid)获得更多信息。

| Name     | Value    | Description                                         |
|----------|----------|-----------------------------------------------------|
| xs       | 100%     | Don't set the grid width for xs screens             |
| sm       | 540px    | Set grid width to 540px when (min-width: 576px)     |
| md       | 720px    | Set grid width to 720px when (min-width: 768px)     |
| lg       | 960px    | Set grid width to 960px when (min-width: 992px)     |
| xl       | 1140px   | Set grid width to 1140px when (min-width: 1200px)   |


## 网格属性

网格默认占有100%的屏幕尺寸并且列之间有间隔。有两个属性可以用来调整这个行为：

| Property        | Description                                                                      |
|-----------------|----------------------------------------------------------------------------------|
| no-padding      | Removes padding from the grid and immediate children columns.                    |
| fixed           | Set a max width based on the screen size.                                        |


## 默认breakpoints

默认breakpoints由`--ion-grid-breakpoints` CSS变量定义。可以通过不同的值去定制breakpoint，重命名以及添加/移除breakpoints。参见[定制网格](#customizing-the-grid)获得更多信息。

| Name     | Value    | Width Prefix | Offset Prefix | Push Prefix  | Pull Prefix | Description                                       |
|----------|----------|--------------|---------------|--------------|-------------|---------------------------------------------------|
| xs       | 0        | `size-`      | `offset-`     | `push-`      | `pull-`     | Set columns when (min-width: 0)                   |
| sm       | 576px    | `size-sm-`   | `offset-sm-`  | `push-sm-`   | `pull-sm-`  | Set columns when (min-width: 576px)               |
| md       | 768px    | `size-md-`   | `offset-md-`  | `push-md-`   | `pull-md-`  | Set columns when (min-width: 768px)               |
| lg       | 992px    | `size-lg-`   | `offset-lg-`  | `push-lg-`   | `pull-lg-`  | Set columns when (min-width: 992px)               |
| xl       | 1200px   | `size-xl-`   | `offset-xl-`  | `push-xl-`   | `pull-xl-`  | Set columns when (min-width: 1200px)              |


## 自动布局列

### 等宽

列默认会对所有设备和屏幕大小进行等分占用。

```html
<ion-grid>
  <ion-row>
    <ion-col>
      <div>
        1 of 2
      </div>
    </ion-col>
    <ion-col>
      <div>
        2 of 2
      </div>
    </ion-col>
  </ion-row>
  <ion-row>
    <ion-col>
      <div>
        1 of 3
      </div>
    </ion-col>
    <ion-col>
      <div>
        2 of 3
      </div>
    </ion-col>
    <ion-col>
      <div>
        3 of 3
      </div>
    </ion-col>
  </ion-row>
</ion-grid>
```

### 设定单列宽度

设置单列的宽度，则其它列会根据它自动调整大小。可以通过我们的预定义网格属性来实现。在下面的例子中，不管中间那列的宽度怎么变化，其它的列都会自动调整。

```html
<ion-grid>
  <ion-row>
    <ion-col>
      <div>
        1 of 3
      </div>
    </ion-col>
    <ion-col size="8">
      <div>
        2 of 3 (wider)
      </div>
    </ion-col>
    <ion-col>
      <div>
        3 of 3
      </div>
    </ion-col>
  </ion-row>
  <ion-row>
    <ion-col>
      <div>
        1 of 3
      </div>
    </ion-col>
    <ion-col size="6">
      <div>
        2 of 3 (wider)
      </div>
    </ion-col>
    <ion-col>
      <div>
        3 of 3
      </div>
    </ion-col>
  </ion-row>
</ion-grid>
```

### 变长

通过设置`size-{breakpoint}`属性为`"auto"`，列可以基于内容的实际宽度进行调整。这对于以像素设置列宽尤其有用。变长列相邻的列会自动调整宽度来填充行。

```html
<ion-grid>
  <ion-row>
    <ion-col>
      <div>
        1 of 3
      </div>
    </ion-col>
    <ion-col size="auto">
      <div>
        Variable width content
      </div>
    </ion-col>
    <ion-col>
      <div>
        3 of 3
      </div>
    </ion-col>
  </ion-row>
  <ion-row>
    <ion-col>
      <div>
        1 of 4
      </div>
    </ion-col>
    <ion-col>
      <div>
        2 of 4
      </div>
    </ion-col>
    <ion-col size="auto">
      <div>
        <ion-input placeholder="Variable width input"></ion-input>
      </div>
    </ion-col>
    <ion-col>
      <div>
        4 of 4
      </div>
    </ion-col>
  </ion-row>
</ion-grid>
```


## 响应式属性

### 所有breakpoints

要定制所有设备和屏幕的列尺寸，设置`size`属性。该属性的值决定占有所有有效总列数中的多少列。

```html
<ion-grid>
  <ion-row>
    <ion-col size="4">
      <div>
        1 of 4
      </div>
    </ion-col>
    <ion-col size="2">
      <div>
        2 of 4
      </div>
    </ion-col>
    <ion-col size="2">
      <div>
        3 of 4
      </div>
    </ion-col>
    <ion-col size="4">
      <div>
        4 of 4
      </div>
    </ion-col>
  </ion-row>
</ion-grid>
```

### 水平堆砌

联合使用宽度和breakpoint属性创建网格系统，可以使它从最小屏开始堆积，然后再变成小屏幕。

```html
<ion-grid>
  <ion-row>
    <ion-col size="12" size-sm>
      <div>
        1 of 4
      </div>
    </ion-col>
    <ion-col size="12" size-sm>
      <div>
        2 of 4
      </div>
    </ion-col>
    <ion-col size="12" size-sm>
      <div>
        3 of 4
      </div>
    </ion-col>
    <ion-col size="12" size-sm>
      <div>
        4 of 4
      </div>
    </ion-col>
  </ion-row>
</ion-grid>
```


## 重新排列

### 列位移

将列移到右侧，需要添加`offset`属性。该属性通过设置指定列数来增加列左侧的空白。举例，下面网格最后一列会移动3列并且占用3列：

```html
<ion-grid>
  <ion-row>
    <ion-col size="3">
      <div>
        1 of 2
      </div>
    </ion-col>
    <ion-col size="3" offset="3">
      <div>
        2 of 2
      </div>
    </ion-col>
  </ion-row>
</ion-grid>
```

Offsets也能依据屏幕breakpoints设置。下面的例子，最后1列将会对`md`及以上屏幕位移3列：

```html
<ion-grid>
  <ion-row>
    <ion-col size-md="3">
      <div>
        1 of 3
      </div>
    </ion-col>
    <ion-col size-md="3">
      <div>
        2 of 3
      </div>
    </ion-col>
    <ion-col size-md="3" offset-md="3">
      <div>
        3 of 3
      </div>
    </ion-col>
  </ion-row>
</ion-grid>
```

### Push和pull

通过添加`push`和`pull`属性对列进行重排。这两个属性通过指定列数量来调节`left`和`right`，非常方便重排列。例如，下面网格中列描述为`1 of 2`的这列将会是最后一列，而`2 of 2`的则将会是第一列。

```html
<ion-grid>
  <ion-row>
    <ion-col size="9" push="3">
      <div>
        1 of 2
      </div>
    </ion-col>
    <ion-col size="3" pull="9">
      <div>
        2 of 2
      </div>
    </ion-col>
  </ion-row>
</ion-grid>
```

Push和pull也可以基于屏幕breakpoint添加。下面的例子中，列描述为`3 of 3`在`md`及以上屏中实际上应该排在第一列：

```html
<ion-grid>
  <ion-row>
    <ion-col size-md="6" push-md="3">
      <div>
        1 of 3
      </div>
    </ion-col>
    <ion-col size-md="3" push-md="3">
      <div>
        2 of 3
      </div>
    </ion-col>
    <ion-col size-md="3" pull-md="9">
      <div>
        3 of 3
      </div>
    </ion-col>
  </ion-row>
</ion-grid>
```


## 对齐

### 垂直对齐

通过添加不同的行属性，所有行内的列可以进行垂直对齐。详细的属性列表，请参见[使用CSS](/docs/layout/css-utilities#flex-container-properties)。

```html
<ion-grid>
  <ion-row align-items-start>
    <ion-col>
      <div>
        1 of 4
      </div>
    </ion-col>
    <ion-col>
      <div>
        2 of 4
      </div>
    </ion-col>
    <ion-col>
      <div>
        3 of 4
      </div>
    </ion-col>
    <ion-col>
      <div>
        4 of 4 <br>
        # <br>
        # <br>
        #
      </div>
    </ion-col>
  </ion-row>

  <ion-row align-items-center>
    <ion-col>
      <div>
        1 of 4
      </div>
    </ion-col>
    <ion-col>
      <div>
        2 of 4
      </div>
    </ion-col>
    <ion-col>
      <div>
        3 of 4
      </div>
    </ion-col>
    <ion-col>
      <div>
        4 of 4 <br>
        # <br>
        # <br>
        #
      </div>
    </ion-col>
  </ion-row>

  <ion-row align-items-end>
    <ion-col>
      <div>
        1 of 4
      </div>
    </ion-col>
    <ion-col>
      <div>
        2 of 4
      </div>
    </ion-col>
    <ion-col>
      <div>
        3 of 4
      </div>
    </ion-col>
    <ion-col>
      <div>
        4 of 4 <br>
        # <br>
        # <br>
        #
      </div>
    </ion-col>
  </ion-row>
</ion-grid>
```

不同列也可以添加不同的对齐属性，通过在列上面添加对齐属性来实现。详细的属性列表，请参见[使用CSS](/docs/layout/css-utilities#flex-item-properties)。

```html
<ion-grid>
  <ion-row>
    <ion-col align-self-start>
      <div>
        1 of 4
      </div>
    </ion-col>
    <ion-col align-self-center>
      <div>
        2 of 4
      </div>
    </ion-col>
    <ion-col align-self-end>
      <div>
        3 of 4
      </div>
    </ion-col>
    <ion-col>
      <div>
        4 of 4 <br>
        # <br>
        # <br>
        #
      </div>
    </ion-col>
  </ion-row>
</ion-grid>
```

### 水平对齐

通过添加不同的行属性可以设置列的水平对齐。详细的属性列表，请参见[使用CSS](/docs/layout/css-utilities#flex-container-properties)。

```html
<ion-grid>
  <ion-row justify-content-start>
    <ion-col size="3">
      <div>
        1 of 2
      </div>
    </ion-col>
    <ion-col size="3">
      <div>
        2 of 2
      </div>
    </ion-col>
  </ion-row>

  <ion-row justify-content-center>
    <ion-col size="3">
      <div>
        1 of 2
      </div>
    </ion-col>
    <ion-col size="3">
      <div>
        2 of 2
      </div>
    </ion-col>
  </ion-row>

  <ion-row justify-content-end>
    <ion-col size="3">
      <div>
        1 of 2
      </div>
    </ion-col>
    <ion-col size="3">
      <div>
        2 of 2
      </div>
    </ion-col>
  </ion-row>

  <ion-row justify-content-around>
    <ion-col size="3">
      <div>
        1 of 2
      </div>
    </ion-col>
    <ion-col size="3">
      <div>
        2 of 2
      </div>
    </ion-col>
  </ion-row>

  <ion-row justify-content-between>
    <ion-col size="3">
      <div>
        1 of 2
      </div>
    </ion-col>
    <ion-col size="3">
      <div>
        2 of 2
      </div>
    </ion-col>
  </ion-row>
</ion-grid>
```


## 定制网格

通过我们内建的CSS变量，能够更改预置的网格属性。更改间隔的值，列数目，等等。


### 列数目

列数目可以通过`--ion-grid-columns` CSS变量进行修改。默认有12个栅格列，但这个值可以更改为任意正整数，为每个独立列计算实际宽度。

```css
--ion-grid-columns:               12;
```


### 网格留白

网格留白容器可以通过`--ion-grid-padding` CSS变量对所有breakpoints进行设置。要覆盖单独的某个breakpoint，使用`--ion-grid-padding-{breakpoint}` CSS变量。


```css
--ion-grid-padding:               5px;

--ion-grid-padding-xs:            5px;
--ion-grid-padding-sm:            5px;
--ion-grid-padding-md:            5px;
--ion-grid-padding-lg:            5px;
--ion-grid-padding-xl:            5px;
```


### 网格宽度

要更改网格对于屏幕大小的定义，覆盖不同breakpoint所对应的`--ion-grid-width-{breakpoint}`值。

```css
--ion-grid-width-xs:              100%;
--ion-grid-width-sm:              540px;
--ion-grid-width-md:              720px;
--ion-grid-width-lg:              960px;
--ion-grid-width-xl:              1140px;
```


### 列留白

要更改所有breakpoint的列留白，通过设置`--ion-grid-column-padding` CSS变量实现。要覆盖单独的breakpoint，则使用`--ion-grid-column-padding-{breakpoint}` CSS变量实现。


```css
--ion-grid-column-padding:        5px;

--ion-grid-column-padding-xs:     5px;
--ion-grid-column-padding-sm:     5px;
--ion-grid-column-padding-md:     5px;
--ion-grid-column-padding-lg:     5px;
--ion-grid-column-padding-xl:     5px;
```
