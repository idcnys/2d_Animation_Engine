
# 2d Animation Engine - With HTML5 Canvas API

A lightweight **JavaScript canvas animation engine** for drawing and animating mathematical objects such as:

* Lines
* Circles
* Rectangles
* Dots
* Graphs
* Coordinate systems
* Text
* Animated movements

The engine also supports **task-based rendering**, **step animations**, and **video recording** of the canvas.

---

## Performance Visualization - [video 01](https://github.com/user-attachments/assets/9179ee0a-92d8-4ee0-b13a-e8467cd0e045)

## Performance Visualization - [video 02](https://github.com/user-attachments/assets/6e602df5-575c-4be5-8074-cbe6771da542)



# Overview

* Animated drawing of shapes
* Linear motion animation
* Graph plotting
* Coordinate system rendering
* Arrow tips and dashed lines
* Text and labeled shapes
* Canvas recording to `.webm`
* High-DPI rendering support
* Task queue animation system

---

# Installation

Clone the repository:

```bash
git clone https://github.com/idcnys/2d_Animation_Engine.git
```

Import the module:

```javascript
import {
Colors,
Rectangle,
LinearMotion,
Circle,
Text,
Line,
Dot,
CoordinateSystem,
TextBox,
Parser,
Task,
ArrowTip,
Graph,
MainFrame
} from "./engine.js";
```

---

# Basic Usage

### Create Canvas Engine

```javascript
const engine = new MainFrame("canvas");
```

### Add Objects

```javascript
const rect = new Rectangle(100,100,200,120,"yellow");
const circle = new Circle(400,200,80,"cyan");
const line = new Line(200,300,150,45);

engine.add(rect,circle,line);
```

### Play Animation

```javascript
engine.play();
```

---

# Core Classes

## MainFrame

Main rendering engine.

```javascript
new MainFrame(canvasId, stream=false, filename="canvas-animation", background="#000")
```

Parameters:

| Parameter  | Description           |
| ---------- | --------------------- |
| canvasId   | HTML canvas id        |
| stream     | record animation      |
| filename   | output video filename |
| background | canvas background     |

Methods:

```
add(...objects)
play()
setOrigin(x,y)
remove(object)
```

---

# Shape Objects

## Rectangle

Draws animated rectangles.

```javascript
new Rectangle(x,y,width,height,strokeColor,lineWidth,fill,fillColor,label,labelText,speed)
```

Example:

```javascript
let rect = new Rectangle(200,200,150,100,"yellow");
```

---

## Circle

Draws animated circles.

```javascript
new Circle(cx,cy,radius,strokeColor,fill,fillColor,lineWidth)
```

Example:

```javascript
let c = new Circle(300,300,100,"cyan");
```

---

## Line

Draws animated lines.

```javascript
new Line(x,y,length,angle,strokeColor,label,labelText,dashed,arrowtip,dbltip,speed)
```

Example:

```javascript
let line = new Line(100,200,200,30,"yellow");
```

Features:

* dashed lines
* arrow tips
* double arrow tips
* labels

---

## Dot

Draws points.

```javascript
new Dot(x,y,radius,color)
```

Example

```javascript
let d = new Dot(300,200,5,"red");
```

---

## Text

Draws text on canvas.

```javascript
new Text(text,x,y,color,size,font)
```

Example

```javascript
new Text("Hello",200,150,"white","20px","Arial")
```

---

## TextBox

Text with a surrounding box.

```javascript
new TextBox(text,x,y,textcolor,boxcolor,angle)
```

---

# Coordinate System

Draws a graph coordinate system with ticks.

```javascript
new CoordinateSystem(x,y,labeled,spacing)
```

Example

```javascript
let graph = new CoordinateSystem(400,300,true,20);
```

Features

* origin point
* tick marks
* optional labels

---

# Graph Plotting

Plot mathematical functions.

```javascript
new Graph(expression,color,minX,maxX,step,scale)
```

Example

```javascript
let g = new Graph(
x => Math.sin(x),
"lime",
-360,
360,
1,
100
);
```

---

# Animations

## Linear Motion

Moves objects linearly.

```javascript
new LinearMotion(object,direction,distance)
```

Directions:

```
right
left
up
down
```

Example

```javascript
let rect = new Rectangle(100,100,100,80);

let move = new LinearMotion(rect,"right",300);

engine.add(rect);
engine.add(move);
```

---

# Colors

The `Colors` class contains predefined color constants.

Example:

```javascript
const colors = new Colors();

colors.BLUE
colors.RED
colors.GREEN
colors.GOLD
```

---

# Parser

Utility class for coordinate translation.

```javascript
new Parser(originX,originY)
```

Used to convert coordinates relative to origin.

---

# Video Recording

The engine can record animations.

```javascript
const engine = new MainFrame(
"canvas",
true,
"animation"
);
```

After animation finishes a `.webm` file downloads automatically.

---

# Example

```javascript
const engine = new MainFrame("canvas");

const rect = new Rectangle(100,100,200,120,"yellow");
const circle = new Circle(500,300,80,"cyan");
const line = new Line(200,200,300,45,"white",true,"Diagonal");

engine.add(rect,circle,line);

engine.play();
```

---

# Rendering Pipeline

The engine works using a **task queue**.

Steps:

1. Objects are added to the task queue
2. Each task animates sequentially
3. Engine waits until animation completes
4. Next task begins

Internal flow:

```
add() -> task queue -> animation step -> completion -> next task
```

---

# Exported Modules

```
Colors
Rectangle
LinearMotion
Circle
Text
Line
Dot
CoordinateSystem
TextBox
Parser
Task
ArrowTip
Graph
MainFrame
```
