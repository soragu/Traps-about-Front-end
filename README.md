## Compatibility

### Chrome

#### 1. Minimuns font size
Some versions of Chrome default minimum font size is 12px

### Safari
#### 1. Construtor about Date type
```
new Date("2014-03-09");  // "invalid date"
```
The pattern yyyy-MM-dd isn't an officially supported format for Date constructor. Firefox and Chrome seems to support it, but don't count on other browsers doing the same.
**Here are some of supported strings:**
MM-dd-yyyy
yyyy/MM/dd
MM/dd/yyyy
MMMM dd, yyyy
MMM dd, yyyy

### FireFox
####1. Input
Firefox automatically adds the line-height property to the `<input type="button">`, and you can not customize the style to override it!

### IE

## Coding

### Javascript

#### 1. Global variable
Always use the `var` keyword for the first time when assigning values to variables. Avoid creating global variables implicitly.
Example following here:
```
function foo() {
    var a = b = 0;
    // body...
}
```
It is a trap. Variable `b` is global here. Why? Because assignment operations are from right to left.

#### 2. Variable Declaration
```
if ("a" in window) {
	var a = 1;
 } 
console.log(a); // undefined or 1 ?
```
It is a trap. The answer is 1. Why? Because declarations are parsed to the top of the scope.

#### 3. Function expression
```
var bar = function foo() {
    foo(); // It work
};
 
foo(); // erroe：ReferenceError
```
#### 4. Closure in Loop
Example:
```
<!doctype html>
<html lang="en">
<head>
    <meta charset="UTF-8">
    <title>Document</title>
</head>
<body>
    <h3>when clicking links below, show the number of its sequence</h3>
    <ul>
        <li><a href="#">link #0</a></li>
        <li><a href="#">link #1</a></li>
        <li><a href="#">link #2</a></li>
        <li><a href="#">link #3</a></li>
        <li><a href="#">link #4</a></li>
    </ul>
    <script type="text/javascript">
    	var links = document.getElementsByTagName("ul")[0].getElementsByTagName("a");
 
		for (var i = 0, l = links.length; i < l; i++) {
		    links[i].onclick = function (e) {
			e.preventDefault();
			alert("You click link #" + i);
		    } 
		}
    </script>
</body>
</html>
```
When you click each link, it always showing 5. Because `i` be changed to 5 after the loop.

### CSS

#### 1. Horizontal Centers
* When element is `position:static;`and child block element with fixed width, just use `margin:0 auto;` on chlid element.

* When element is `position:absolute;` and with fixed width, just use `left:50%; margin-left:-(width/2);`.

* When parent element is `display:flex;`, parent just use `justify-content: center;`.

* When the element is inline, parent just use `text-align: center;`.

* When parent width is percentage, parent use `padding-left` `padding-right`.

#### 2. Vertical Centers
* When element is `position:static;` and with fixed height, just use `top:50%; margin-top:-(height/2);`.

* When parent element is `display:flex;`, parent just use `align-item:center`.

* When element is inline, parent just use `text-align:center`.

* When element height is percetage, just use `padding-top` `padding-bottom`.

* If just making text with simple horizonal center, set `line-height` equal to parent's `height`.

#### 3. Canvas
* Size of Canvas only support `px` unit. Image will distort when using css style handle width and height. Please use `width` and `height` attributes like this `$(‘canvas’)[0].width = 100 ;$(‘canvas’)[0].height = 300` or this `<canvas width=100 height=300>`. 

#### 4. Position
* `position:absolute;`will ignore `padding`.

* Don’t set width: 100%; on an element that has `position: [absolute|fixed];`, left, and right. The use of `width: 100%;` is the same as the combined use of `left: 0; and right: 0;`. Use one or the other, but not both.

* When a `position: fixed;` element's parent set `transform` property, the browser will break `position: fixed` resolution.

#### 5. Background
* Even if `body` has `width` and `height`, body's `background` always cover whole screen.

* `background-position: center` and `background-size` can be used to make background has been centered and width or height adaptivly.

#### 6. Box Model
* When the element has setted `padding` and `border-width`, the actual width of the element is wider than `width` setting. In order to avoid this embarrassing problem, we can use `box-sizing: border-box;` to re-set the box model calculation range.

#### 7. Bug
* The browser will automatically add a blank character to the end of the `:inline-block` element. It could change `font-size` to zero for fixing this issue.