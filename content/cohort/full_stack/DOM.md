---
id: DOM
aliases: []
tags: []
---

## Creating HTML element

- create element method
```javascript
const para = document.createElement("p");
para.innerText = "This is a paragraph via DOM";
document.body.appendChild(para);
```

## Finding HTML element
```javascript
//elements by ID
var firstDiv = document.getElementById("first");
//elements by tag
var divs = document.getElementByTagname("div");
//elements by class
var divs = document.getElementByClassName("intro");
//elements by CSS selectors
var paragraphs = document.querySelectorAll('p');
paragraphs.forEach(paragraph => paragraph.style.backgroundColor='blue')
//elements by HTML object collections
const x = document.forms["frm1"];
let text = "";
for(let i=0;i<x.length;i++){
    text += x.elements[i].value+'<br>';
}
document.getElementById("demo").innerHTML = text;
```
## Other elements
```javascript
// document.anchors
document.getElementById("demo").innerHTML =
"Number of anchors are: " + document.anchors.length;
//document.body
document.getElementById("demo").innerHTML = document.body.innerHTML;
//document.documentElement
document.getElementById("demo").innerHTML = document.documentElement.innerHTML;
//document.embeds
//document.forms
//document.head
//document.images
//document.links
//document.scripts
//document.title
```
## Changing HTML Elements
```javascript
//Property
element.innerHTML = //new HTML content
element.attribute = //new value
element.style.property = //new style
//Method
element.setAttribute(Attribute,value);
```
# Dynamic HTML content
## adding and deleting element
```javascript
// create an HTML element
document.createElement(element);
//Remove an Element
document.removeChild(element);
// add an HTML element
document.appendChild(element);
// replacing an HTML element
document.replaceChild(element);
// writing into an html stream
document.write(text);
```
# node method
```javascript
// access child nodes of selected parent
node.childNodes
// access first child of selected parent
node.fistChild
// access last child of selected parent
node.lastChild
// access parent nodes of selected child node
node.parentNode
// access next consecutive element of selected element
node.nextSibling
// access previous consecutive element of selected element
node.previousSibling
```
# events
```javascript
//onclick
<h2 onclick = "this.innerHTML = 'OOPS!'">Click me!</h2>
//oninput
<input type="text" id="fname" oninput = "upperCase()">
//onmouse
<div onmouseover = "mOver(this)" onmouseout = "mOut(this)" >
<div onmouseup = "mUp(this)" onmousedown = "mDown(this)">
```
## eventListener
```javascript
//addEventListener(event,function,useCapture);
document.getElementById("DIV").addEventListener('mousemove',function(){
    document.getELementById("demo").innerHTML = Math.random();
});
//removeEventListener(event,function);
document.getElementById("DIV").removeEventListener('mousemove',function(){
    document.getELementById("demo").innerHTML = Math.random();
});
```

## Bubbling and Capturing
```javascript
//bubbling: inner-most element -> outer-most element
document.getElementById("DIV").removeEventListener('click',function(){
    alert("This is inner element");
}, false);
document.getElementById("DIV").removeEventListener('click',function(){
    alert("This is outer element");
}, false);
//capturing: outer-most element -> inner-most element
document.getElementById("DIV").removeEventListener('click',function(){
    alert("This is inner element");
}, true);
document.getElementById("DIV").removeEventListener('click',function(){
    alert("This is outer element");
}, true);
```
# virtual DOM
