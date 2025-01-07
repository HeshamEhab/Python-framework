# JavaScript in Our Framework

## Why Use JavaScript?
JavaScript is a powerful and versatile programming language that allows you to add interactivity and dynamic functionality to your web applications. By using JavaScript in our framework, you can:

- Respond to user actions in real-time (e.g., clicks, form submissions, or input changes).
- Dynamically update content without reloading the page.
- Communicate with the server to fetch or send data using AJAX.
- Enhance the overall user experience with smooth animations and interactive elements.

## Including JavaScript Files in Your Python File
To integrate JavaScript into your app, the JavaScript file should be stored in a specific directory structure relative to your Python file.

### Directory Structure:
If your Python file is located in:
`ins_apps -> app_blog`

Then the JavaScript file should be located in:
`ins_web -> ins_apps -> app_blog`

### Including the JavaScript File:
To include your JavaScript file in the application, add the following line inside the `out` method of your Python file:

```python
self.app._include("script.js")
```

## Using JavaScript in the Framework

### Selectors
To interact with elements in your HTML, use the `ins` selector:

```javascript
ins("select.src_area")
```

- **Explanation**: The selector inside the parentheses is a standard CSS selector. For example:
  - `select.src_area` refers to a `<select>` element with the class `src_area`.
  - Use `.` for classes and `#` for IDs as in standard CSS selectors.

### Events
Events define when an action should occur. You can attach an event to your selector using the `._on` method. For example:

```javascript
._on("change")
```

Here is a list of commonly used events:
- `change`: Triggered when a form element’s value changes.
- `click`: Triggered when the element is clicked.
- `mouseover`: Triggered when the mouse hovers over the element.
- `mouseout`: Triggered when the mouse leaves the element.
- `keyup`: Triggered when a key is released.
- `keydown`: Triggered when a key is pressed.
- `scroll`: Triggered when the user scrolls.
- `submit`: Triggered when a form is submitted.

You can find more events [here](https://www.w3schools.com/jsref/dom_obj_event.asp).

### Actions
Actions define what happens when the event occurs. For example:

```javascript
function(o){
    console.log("My code works");
}
```

### Complete Example
Here’s how to combine the selector, event, and action into a functional piece of code:

```javascript
ins("select.src_area")._on("change", function(o){
    console.log("My code works");
}, true);
```

#### Notes:
- The `o` variable represents the object where the event occurred.
- If the class is used in multiple objects, `o` allows you to target the specific object that triggered the event.

### Passing Data with Attributes
To pass data from an HTML element to JavaScript, use the `data-*` attributes. For example:

#### HTML:
```html
<select class="src_area" data-id="123"></select>
```

#### JavaScript:
```javascript
o._getData("id");
```
This retrieves the value of the `data-id` attribute (e.g., `123`).

## AJAX
### What is AJAX?
AJAX (Asynchronous JavaScript and XML) allows you to communicate with the server without reloading the page. It is essential for creating dynamic and responsive web applications.

### Why Use AJAX?
- Fetch or send data to the server without refreshing the page.
- Improve user experience with faster interactions.
- Enable real-time updates in your app.

### Using AJAX in Our Framework

#### Define the Method
First, call the desired method from the Python file. For example:

```javascript
ins("_get_js_data")
```

#### Specify the Library
Define the type of AJAX operation based on the part of the application you’re working on. For example:

```javascript
._ajax._app
```
Replace `app` with the relevant section, such as `wdgt` for widgets.

#### Pass Data
Prepare the data to send to the server. For example:

```javascript
{"id": o._getData("id")}
```
This sends the `id` value retrieved from the object using the `o._getData` method.

#### Handle the Response
Specify the actions to perform after the server responds. For example:

```javascript
function(data){
    console.log("Operation done");
}
```

### Complete AJAX Example
Here’s how to put it all together:

```javascript
ins("_get_js_data")._ajax._app({"id": o._getData("id")}, function(data){
    console.log("Operation done");
});
```

#### Explanation:
1. **Selector**: `ins("_get_js_data")` specifies the method to call.
2. **Data**: `{ "id": o._getData("id") }` sends the `id` to the server.
3. **Callback**: `function(data)` handles the server’s response.

### Notes:
- The `data` parameter in the callback contains the server’s response.
- Use this response to update the UI, show notifications, or take other actions.
