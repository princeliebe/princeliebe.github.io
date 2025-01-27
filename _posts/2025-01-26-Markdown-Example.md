# Hi
This is a website for learning HTML, JS, and CSS.
# What is HTML?
HTML stands for HyperText Markup Language, and it's the language designed for webpages. Almost every website uses HTML.
# Need an example?
Here's an example of HTML:
```HTML
<!DOCTYPE html>
<html>
<head>
    <title>Hello, World!</title>
</head>
<body>
    <h1>Hello, World!</h1>
    <p>This is my first HTML page.</p>
</body>
</html>
```

Click [here](#) for the output.
# JavaScript
JavaScript, shortened as JS, is a programming language to make your HTML pages more functional. Templates are below.
```JS
// Create an element
const myNewElement = document.createElement("p");
myNewElement.innerText = "Hi!";
document.body.appendChild(myNewElement);
```
```JavaScript
// Change properties
const myElement = document.getElementById('example-element');
myElement.innerText = "SHH!";
```
# CSS
CSS is to style your pages with properties and things. It's not required, but you could embed CSS using the `<style>` tag or the `<link>` tag. For example, if you want to import your stylesheet like this: `<link rel="stylesheet" href="styles.css" />`
# Full example
```HTML
<html>
<head>
    <style src="details.css">
    <title>My Web</title>
    <script src="javascript-goes-here.js">
</head>
<body>
    <button onclick="createText()">Click Me!</button>
    <p id="change-the-text-of-this"></p>
</body>
</html>
```
