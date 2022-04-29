### Handling Events
[Link to Lesson](https://www.coursera.org/learn/html-css-javascript-for-web-developers/lecture/hlzS7/lecture-54-handling-events)

        Old HTML Doccument:

```html
    <!DOCTYPE html>
    <html lang="en">
    <head>
        <meta charset="UTF-8">
    </head>
    <body>
        <h1 id="title">Lecture 53</h1>
        <p>
            Say hello to
            <input id="name" type="text">

            <button onclick="sayHello();">
                Say it!
            </button>

        </p>
        <div id="content"></div>
        <script src="js/script.js"></script>
    </body>
    </html>
```
> By removing the button inner fuctions, js have to implement that function using the 'button' event.


        New HTML Document without button tag inner function:

```html
    <!DOCTYPE html>
    <html lang="en">
    <head>
        <meta charset="UTF-8">
        <script src="js/script.js"></script>
    </head>
    <body>
        <h1 id="title">Lecture 53</h1>
        <p>
            Say hello to
            <input onblur="sayHello();" id="name" type="text">
            
            <button>
                Say it! 
            </button>

        </p>
        <div id="content"></div>
    </body>
    </html>
```
        New Script that handles the button event:
```js
    document.addEventListener("DOMContentLoaded",
        function(event) { // event that surrounds the button inner code

            function sayHello(event) {
                this.textContent = "Said it!";
                var name =
                    document.getElementById("name").value;
                var message = "<h2>Hello " + name + "!</h2>";

                document
                    .getElementById("content")
                    .innerHTML = message;

                if (name === "student") {
                    var title =
                        document
                        .querySelector("#title")
                        .textContent;
                    title += " & Lovin' it!";
                    document
                        .querySelector("h1")
                        .textContent = title;
                }
            }

            // Unobtrusive event binding
            document.querySelector("button")
                .addEventListener("click", sayHello);

        }
    );
``` 