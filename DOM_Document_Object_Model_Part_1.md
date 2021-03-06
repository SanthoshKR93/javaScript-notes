
# DOM-DOCUMENT OBJECT MODEL

For displaying an HTML file on the browser, the browser builds a logical object oriented model which represents the elements of html as a tree structure, this is called Document Object Model.
JavaScript can be used to add, delete or modify these elements dynamically.

The document object model/representation is a tree structure representation.
we can represent an HTML page as a tree where the root of the tree structure is the Document object. 
The nodes have parent and child nodes.
```


                                                          Document object
                                                                 |
                                                                 |
                                            -------------------<html>--------------------
                                            |                                           |
                                            |                                           |
                                          <head>                             ---------<body>---------
                                            |                                |                      |
                                            |                                |                      |
                                          <title>                           <h1>                   <a>

```

```
root---> Document object
<html> has 2 child nodes head and body
head has a child title and a parent node <html>
body has 2 child nodes <h1>,<a> and a parent node <html>
```
JavaScript can be used to add, delete or modify these elements dynamically by using the "inner HTML" property of the document object.
The inner HTML property of document object dynamically overwrites the contents ie. the contents already inside that html element will be overwrtten.

#### example:
```
document.body.innerHTML("hello world")
```
This code alters the body of HTML and adds the text hello world which gets displayed when the js file is run on the browser.


### SELECTING ELEMENTS

All the elements of the DOM tree representation are objects and they have their own properties.
Selecting desired HTML Elements can be done using three ways:

### get element by 'id'

Syntax:
```      
       document.getElementById("id")
```
where document is the root object in the DOM tree and is used to0 access the HTML elements.

#### example:
```
<html>
<head>
<title>
Get Element By ID
</title>
</head>
<body>
<div id="san">
<p>MY NAME IS SANTHOSH</p>
</div>

<script>
function changeName(){
var a= document.getElementById("san");
var b=a.childNodes;
for(var i=0;i<b.length;i++){
b[i].innerHTML="MY NAME IS KILLBOX";
}
}
setTimeout(changeName,500);
</script>

</body>
</html>
```
### get element by 'classname'

Syntax:
```       
       document.getElementsByClassName("classname")
```
This retrieves all the elements under that particular class in an array format and can be modified by iterating through the elements in the array with the help of a for loop.

#### example:

```
<html>
<head>
<title>
Get Element By ClassName
</title>
</head>
<body>
<div class="san" style="width=200px">
<p>MY NAME IS SANTHOSH</p>
<p>MY NAME IS SANTHOSH</p>
<p>MY NAME IS SANTHOSH</p>
<p>MY NAME IS SANTHOSH</p>
</div>

<script>
function changeName(){
var a = document.getElementsByClassName("san");               // returns an array of elements
a[0].style.width="23px";                                      // since there is only one class in the entire code, it is accessed using a[0]
var b = a[0].childNodes;                                      // retrieving the child nodes of the class "san" as an array of elements.
for(var i=0;i<b.length;i++){
b[i].innerHTML="MY NAME IS KILLBOX";
}
}
setTimeout(changeName,500);                                   // setting a timeout of 500 milliseconds after which the function changeName() is called.
</script>

</body>
</html>
```


### get element by 'tagname'

Syntax:
```
       document.getElementsByTagName("tagname")
```
This retrieves all the elements of a particular tag name specified in an array format each of which can be modified using an iterator variable in a for loop.

#### example:

```
<html>
<head>
<title>
Get Element By TagName
</title>
</head>
<body>
<div>
<p>MY NAME IS SANTHOSH</p>
<p>MY NAME IS SANTHOSH</p>
<p>MY NAME IS SANTHOSH</p>
<p>MY NAME IS SANTHOSH</p>
</div>

<script>
function changeName(){
var a = document.getElementsByTagName("p");
for(var i=0;i<a.length;i++){
a[i].innerHTML="MY NAME IS KILLBOX";
}
}
setTimeout(changeName,500);
</script>

</body>
</html>
```

### OTHER PROPERTIES OF ELEMENTS

Refer this HTML code for all the examples below:

```
<html>
<body>
<div class=name>
<p><span>MY NAME IS SANTHOSH</span></p>
<p>MY NAME IS ARJUN</p>
<p>MY NAME IS YADU</p>
<p>MY NAME IS SREERAJ</p>
</div>
</body>
</html>
```
### childNodes

Syntax:
```
      element.childNodes;               // retrieves the child nodes of the current element.
```
#### example:

```
<script>
function changeName(){
var a = document.getElementsByClassName("name");
var b=a[0].childNodes
for(var i=0;i<b.length;i++){
b[i].innerHTML="MY NAME IS KILLBOX";
}
}
setTimeout(changeName,500);
</script>
```
### parentNode
   
Syntax:
```
      element.parentnode                    // retrieves the parent node of current element.
```

#### example:

```
<script>
function changeName(){
var a=document.getElementsByTagName("p");
a[0].innerHTML=a[0].parentNode;
}
setTimeout(changeName,500);
</script>
```
### nextSibling

Syntax:

```
       element.nextSibling                // retrieves the next sibling of the current element in the same level.
```
#### example:

```
<html>
<body>
<div class=name>
<p>MY NAME IS SANTHOSH</p><p>MY NAME IS SANTHOSH</p><p>MY NAME IS SANTHOSH</p><p>MY NAME IS SANTHOSH</p>
</div>

<script>
function changeName(){
var a=document.getElementsByTagName("p");
a[0].innerHTML=a[0].nextSibling.innerHTML;
}
setTimeout(changeName,500);
</script>


</body>
</html>
```

### previousSibling

Syntax:

```
       element.previousSibling            // retrieves the previous sibling of the current element in the same level.
```
#### example:

```
<html>
<body>
<div class=name>
<p>MY NAME IS SANTHOSH0</p><p>MY NAME IS SANTHOSH1</p><p>MY NAME IS SANTHOSH2</p><p>MY NAME IS SANTHOSH3</p>
</div>

<script>
function changeName(){
var a=document.getElementsByTagName("p");
a[1].innerHTML=a[1].previousSibling.innerHTML;
}
setTimeout(changeName,500);
</script>


</body>
</html>
```
### firstChild

Syntax:

```
       element.firstChild                 // retrieves the first child of the current element.
```
#### example:

```
<html>
<body>
<ul id="name"><li>MY NAME IS SANTHOSH</li><li>MY NAME IS ARJUN</li><li>MY NAME IS YADU</li><li>MY NAME IS SREERAJ</li></ul>
<div id="demo"></div>
<script>
function changeName(){
var a=document.getElementById("name");
document.getElementById("demo").innerHTML=a.firstChild.innerHTML;
}setTimeout(changeName,500);
</script>

</body>
</html>
```
### lastChild

Syntax:

```
       element.lastChild                  // retrieves the first child of the current element.
```
#### example:

```
<html>
<body>
<ul id="name"><li>MY NAME IS SANTHOSH</li><li>MY NAME IS ARJUN</li><li>MY NAME IS YADU</li><li>MY NAME IS SREERAJ</li></ul>
<div id="demo"></div>
<script>
function changeName(){
var a=document.getElementById("name");
document.getElementById("demo").innerHTML=a.lastChild.innerHTML;
}setTimeout(changeName,500);
</script>

</body>
</html>
```
### hasChildNodes

Syntax:

```
      element.hasChildNodes;              // checks whether the current element has child nodes or not (Boolean result :True or False)
```
#### example:

```
<html>
<body>
<ul id="name"><li>MY NAME IS SANTHOSH</li><li>MY NAME IS ARJUN</li><li>MY NAME IS YADU</li><li>MY NAME IS SREERAJ</li></ul>
<script>
function haschildnodes(){
var a=document.getElementById("name");
if(a.hasChildNodes)
{
document.body.innerHTML=`element ${a} has child nodes`;
}
else
{
document.body.innerHTML=`element ${a} has no child nodes`;
}
}setTimeout(haschildnodes,500);
</script>

</body>
</html>
```
### CHANGING ATTRIBUTES

The contents of an element can be changed using 'innerHTML' property of javascript.
Similarly the attributes of an element can be changed.

#### examples:

### Changing the 'src' attribute
Changes the src attribute and replaces its content.
#### example:

```
<html>
<body>
<img id="myimage" src="img01.png" />
<script>
function changeimage(){
var a= document.getElementById("myimage");
a.src="img02.png";
}
setTimeout(changeimage,1000);
</script>
</body>
</html>
```


### Changing the 'href' attribute
Changes the href attribute and replaces its content.
#### example:

```
<html>
<body>
<a id="myimage" href="img01.png" >Click Me</a>
<script>
function changeimage(){
var a= document.getElementById("myimage");
a.href="img02.png";
}
setTimeout(changeimage,5000);
</script>
</body>
</html>
```

### Changing the style elements using style object 

The styles given inside the element can be changed using the style object of javascript.

#### example:

```
<html>
<body>
<img id="myimage" src="img01.png" style="width:200px height:200px"/>
<script>
function changeStyle(){
var a= document.getElementById("myimage");
a.src="img02.png";
a.style.width="500px"
a.style.height="500px"
}
setTimeout(changeStyle,500);
</script>
</body>
</html>
```

## ADDING OR REMOVING ELEMENTS

Elements can be added removed or replaced using different document methods in javascript.


## CREATING ELEMENTS
The following 3 properties can be used for creating elements.

### cloneNodes

Syntax:

```
       element.cloneNode
```
#### example:

```
<html>
<body>
<ul id="name"><li>My name is santhosh1<li><li>My name is santhosh2<li></ul>
<ul id="clone"><li>my name is killbox</li></ul>
<button onclick=cloneelement()>Click Here</button>
<script>
function cloneelement(){
var a= document.getElementById("clone").lastChild;
var d= a.cloneNode(true);
document.getElementById("name").appendChild(d);
}
</script>
</body>
</html>
```

### createTextNode
Syntax:

```
       document.createTextNode("text")
```
#### example:

```
<html>
<body>
<ul id="name"><li>My name is santhosh1<li><li>My name is santhosh2<li></ul>
<ul id="clone"><li>my name is killbox</li></ul>
<button onclick=textnode()>Click Here</button>
<script>
function textnode(){
var a= document.getElementById("clone");
var b= document.createElement("p");
var c= document.createTextNode("MY NAME IS NOT IMPORTANT");
a.appendChild(b.appendChild(c));

document.getElementById("name").appendChild(d);
}
</script>
</body>
</html>
```
### createElement
Syntax:

```
       document.createElement(element)
```
#### example:

```
<html>
<body>
<ul id="name"><li>My name is santhosh1<li><li>My name is santhosh2<li></ul>
<ul id="clone"><li>my name is killbox</li></ul>
<button onclick=textnode()>Click Here</button>
<script>
function textnode(){
var a= document.getElementById("clone");
var b= document.createElement("p");
var c= document.createTextNode("MY NAME IS NOT IMPORTANT");
a.appendChild(b.appendChild(c));

document.getElementById("name").appendChild(d);
}
</script>
</body>
</html>
```

### appendChild
Syntax:

```
       element.appendChild(newnode)
```
#### example:

```
<html>
<body>
<ul id="name"><li>My name is santhosh1<li><li>My name is santhosh2<li></ul>
<ul id="clone"><li>my name is killbox</li></ul>
<button onclick=textnode()>Click Here</button>
<script>
function textnode(){
var a= document.getElementById("clone");
var b= document.createElement("p");
var c= document.createTextNode("MY NAME IS NOT IMPORTANT");
a.appendChild(b.appendChild(c));

document.getElementById("name").appendChild(d);
}
</script>
</body>
</html>
```

### insertBefore
Syntax:

```
       element.insertBefore(node1,node2)    // inserts node1 as child before node2.
```
#### example:

```
<html>
<body>
<ul id="name">
<li>My name is santhosh1<li>
<li>My name is santhosh2<li>
</ul>
<button onclick=textnode()>Click Here</button>
<script>
function textnode(){
var a=document.createElement("li");
var b=document.createTextNode("MY NAME IS NOT IMPORTANT");
a.appendChild(b);
var c=document.getElementById("name");
c.insertBefore(a,c.childNodes[0]);
}
</script>
</body>
</html>
```
## REMOVING ELEMENTS

Removing elements can be done using removeChild method:

### RemoveChild

Syntax:

```
       element.removeChild(node)
```
#### example:

```
<html>
<body>
<ul id="name">
<li id="l1">My name is santhosh1<li>
<li id="l2">My name is santhosh2<li>
</ul>
<button onclick=textnode()>Click Here</button>
<script>
function textnode(){
var c=document.getElementById("name");
var d=document.getElementById("l1");
c.removeChild(d);

}
</script>
</body>
</html>
```
- ### Alternative method by using parentNode property

#### example:

```
<html>
<body>
<ul id="name">
<li id="l1">My name is santhosh1<li>
<li id="l2">My name is santhosh2<li>
</ul>
<button onclick=textnode()>Click Here</button>
<script>
function textnode(){
var d=document.getElementById("l1");
d.parentNode.removeChild(d);                             // using parentNode property

}
</script>
</body>
</html>
```
## REPLACING ELEMENTS
Elements can replaced with other elements using replaceChild method.

### ReplaceChild
Syntax:

```
element.replaceChild(newNode,oldNode)
or
parentNode.replaceChild(newNode,oldNode)
```
#### example:

```
<html>
<body>
<ul id="name">
<li id="l1">My name is santhosh1<li>
</ul>
<button onclick=textnode()>Click Here</button>
<script>
function textnode(){
var a=document.createElement("li");
var b=document.createTextNode("My Name Is Not Important");
a.appendChild(b);
var d=document.getElementById("l1");
d.parentNode.replaceChild(a,d);                             // using parentNode property

}
</script>
</body>
</html>
```
