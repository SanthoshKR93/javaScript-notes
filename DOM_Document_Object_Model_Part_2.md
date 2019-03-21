
## CREATING ANIMATIONS

### setInterval and clearInterval methods

setInterval method is used to set a time interval at which a function given will execute.

Syntax:

```      
       variable = setInterval(function_Name,time_in_milli_seconds)
```
#### example: 
  
  ```
       var t = setInterval(func,500);
```
This means the function func() will get executed every 500 milli seconds.

To stop such an execution at some point, clearTimer method is used.

Syntax:

```
      clearInterval(variable)
```
#### example:

```
      clearInterval(t);
```

#### code:

```
<!DOCTYPE html>
<html>
<head>
<style>
#container{
   width:200px;
   height:200px;
   background-color:yellow;
   position:relative;
}
#box{
   width:50px;
   height:50px;
   background-color:red;
   position:absolute;

}
</style>
</head>
<body>
	 <div id="container">
            <div id="box"> </div>
         </div>

<script>
function anim(){
     var pos = 0; 
    //our box element
    var box = document.getElementById('box');
    var t = setInterval(move, 10);
  
    function move() {
        if(pos >= 150) {
            clearInterval(t);
        }
        else {
            pos += 1;
            box.style.left = pos+'px';  //iterating the position variable so that the the position from left of the box changes w.r.t 'pos' variable.
        }
    }
}
setTimeout(anim,500);
</script>
   </body>
</html>
```
## HANDLING EVENTS

### EVENTS
JavaScript allows us to execute codes when an event occurs.That event can be a mouse click,on window load etc
So when an event occurs on the target element, a handler function is executed.
The following are some of the events in js


### onclick

It occurs when a user clicks on an element.

#### example:

```
<html>
<body>
<button onclick="show()">Click Me</button>
<script>
function show() {
  alert("Hi there");
}
</script>
</body>        
</html>
```

The handlers can also be assigned for elements.
#### example:

```
<html>
	<body>
		<button id="demo">Click Me</button>
<script>	
var a= document.getElementById("demo");
a.onclick=function()
{
document.body.innerHTML=Date();
}
</script>
</body>
</html>
```

### onload and onunload

it occurs when a page loads up or unloads ie. when user opens or closes the page.

#### example:

```
<body onload=dosomething()></body>

or

window.onload=function(){
}
```
For onunload

```
<body onunload=dosomething()></body>

or

window.onunload=function(){
}
```


### onchange

The handler executes a function or piece of code when the content of the element changes.These are mostly used in the case of text-boxes.

<b>Example:</b> converts the lowercase characters to uppercase when the textbox loses focus ie. onchange.

```
<html>
<body>
<input type="text" id="box" onchange="upcase()">
<script>
function upcase(){
var a= document.getElementById("box");
a.value=a.value.toUpperCase();
}

</script>
</body>
</html>
```

### onmouseover and onmouseout

onmouseover means when the mouse is moved over the element.
onmouseout means when the mouse that is moved on to the element is moved out of the element.

#### example:

```
<!DOCTYPE html>
<html>
<body>
<img onmouseover="bigImage(this)" onmouseout="smallImage(this)" border="0" id="img1" src="img01.png" alt="Smiley" width="40" height="40">
<script>
function bigImage(x){
x.style.width="80px";
x.style.height="80px";
}
function smallImage(x){
x.style.width="40px";
x.style.height="40px";
}
</script>
</body>
</html>
```

### onmousedown and onmouseup

onmousedown event means when we click and hold on an element its handler function executes.
onmouseup event means when we release a mouse click on an element, its handler function executes.

#### example:

```
<!DOCTYPE html>
<html>
<body>
<p id="mo" onmousedown="redText()" onmouseup="greenText()">HELLO WORLD</p>
<script>

function redText(){
document.getElementById("mo").style.color="red";
}
function greenText(){
document.getElementById("mo").style.color="green";
}
</script>
</body>
</html>
```

### onblur, onfocus and oninput

- <b>onfocus-</b> when an element is selected, thehandler function is executed.
- <b>onblur-</b>  when an element is unselected or when it loses the focus, the handler function is executed.
- <b>oninput-</b> when an input is given to an element, for eg: a text-box, when input is given, the handler function is executed.

#### example: 

```
<!DOCTYPE html>
<html>
<body>
Enter your name: <input type="text" id="name2" onfocus="myFunction1(this)" onblur="myFunction2(this)" oninput="myFunction3()">
<p id = "name"></p>
<script>
function myFunction1(x) {
  x.style.background = "yellow";
}

function myFunction2(x) {
  x.style.background = "green";
}

function myFunction3() {
var y = document.getElementById("name2").value;
document.getElementById("name").innerHTML="WHAT YOU HAVE WRITTEN SO FAR:" + y;

}

</script>

</body>
</html>
```
### onkeyup and onkeydown

- <b>onkeyup-</b> this event occurs with a keystroke, ie. when we type a character in an text-box, on keyup, the handler function is executed.
onkeydown - this event occurs with a keystroke, ie. when we type a character in an text-box, on keydown, the handler function is executed.

#### example:

```
<!DOCTYPE html>
<html>
<body>
<input type="text" id="uc" onkeyup="uppercase()" onkeydown="display()">
<p id="disp"></p>
<script>

function uppercase(){
var a=document.getElementById("uc");
a.value=a.value.toUpperCase();
}

function display(){
var b=document.getElementById("uc").value;
document.getElementById("disp").innerHTML="What you've typed so far:" + b;
}


</script>
</body>
</html>
```
## EVENT LISTENERS

### addEventListener()

Adding events to an element without making any changes to the current assigned events.

Syntax:

```
       element.addEventListener("event",function_name,useCapture);
```
where, event is the event to be added,
function is the handler function to be executed when the event occurs, 
useCapture is the boolean value given (default value is false) for event bubbling or event capturing.

NOTE: Here when giving an event to be added, the event name is enough 'on'prefix is not needed.

### removeEventListener()
   
Used for removing events assigned to an element.

Syntax:

```
        element.removeEventListener("event",function_name);
```
where event is the event to be removed and function is the handler function assigned at the time of adding the event to the element.

#### example:

```
<!DOCTYPE html>
<html>
<body>
<button id= "name">click here</button>
<script>
var a = document.getElementById("name");
a.addEventListener("click",click);
function click(){
document.body.innerHTML=Date();
a.removeEventListener("click",click);
}
</script>
</body>
</html>
```
### EVENT PROPAGATION
Event Propagation along the parent and child elements are determined using useCapture.
This is used when, there are 2 elements where one element is parent of other, and both of them have events assigned to them, then the useCapture value determines which element's event must be handled first.
there are 2 types :
 
```
element.addEventListener("event",function_name,useCapture);       
```
- <b>Event Bubbling</b>
In event Bubbling, the useCapture value is false.
This means the inner element's event must be handled first.

- <b>Event Capturing</b>
In event capturing, the useCapture value is true.
This means the outer element's event must be handled first.


NOTE: The use capture value is false by default.

#### example : Event Capturing

```
<!DOCTYPE html>
<html>
<body>
<div id="name">
<p id="val">hello world</p>
</div>
<script>
var a = document.getElementById("name");
var b = document.getElementById("val");
a.addEventListener("mouseover",fun1,true);
b.addEventListener("mouseover",fun2,true);
function fun1(){
alert("parent handled first");
}

function fun2(){
alert("child handled second");
}
</script>
</body>
</html>
```

```
result :
parent is handled first then the child. div element first and then p element.
```
#### example: Event Bubbling

```
<!DOCTYPE html>
<html>
<body>
<div id="name">
<p id="val">hello world</p>
</div>
<script>
var a = document.getElementById("name");
var b = document.getElementById("val");
a.addEventListener("mouseover",fun1,false);
b.addEventListener("mouseover",fun2,false);
function fun1(){
alert("parent handled second");
}

function fun2(){
alert("child handled first");
}
</script>
</body>
</html>
```

```
res-->
child is handled first then the parent. 'p' element first and then div element.
```

<b>NOTE:</b> Bubbling goes 'UP' the DOM and Capturing goes 'DOWN' the DOM


## CREATING AN IMAGE SLIDER

#### CODE:

```
<html>
  <head>
    <title>
    Image Slider
    </title>
    <style>
    #container{
    width:"500px";
    height:"550px";
    border:"1px";
    }

    </style>
  </head>
  <body>
    <div id="container" align="center">
    <img id="img" src="img01.png" width="500px" height="500px">
    <button id="btn1" align="right" onclick="next()" >next</button>
    <button id="btn2" align="left" onclick="prev()" >prev</button>
    </div>
    
    <script>
    var i=0; 
    function next()
    {
    var arr = ["img02.png","img04.png","img01.png"];
    var a = document.getElementById("img");
    a.src=arr[i];
    i=i+1;
    
    if(i>=arr.length)
    {
    i=0;
    }
    }


    function prev()
    {
    var arr = ["img02.png","img04.png","img01.png"];
    var a = document.getElementById("img");
    a.src=arr[i];
    i=i-1;
    if(i<0)
    {
    i=arr.length-1;
    }
    }
    

    </script>
  </body>
</html>
```
## FORM VALIDATION

A small example code for showing form validation.

#### code:

```
<html>

  <head>
    
    <title>
    FORM VALIDATION
    </title>
  
  </head>
  
  <body>
   
    <p>Enter a number between 0 and 10:</p>
    <input type="text" id="num">
    <button id="btn" onclick="func()" >Submit</button>
    <p id="disp"></p>
    
    <script>
    function func(){
    var a=document.getElementById("num").value;
    if(a<10 && a>0)
    {
    text="yay!! valid input";
    }
    else{
    text="oops!! invalid input \n try again"; 
    }
    document.getElementById("disp").innerHTML=text;
    }
    </script>
  
  </body>
</html>
```


