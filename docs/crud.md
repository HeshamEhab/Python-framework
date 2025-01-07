## What is a CRUD System?
A CRUD system allows you to manage data in your app with four basic functions:
- **Create**: Add new records.
- **Read**: View existing records.
- **Update**: Edit records.
- **Delete**: Remove records.

### Why Use CRUD?
It makes database tasks easy by creating a user-friendly interface for these functions.

With CRUD, you can:
- Show a list of data.
- Add new items.
- Edit or delete items.
- Filter data to find what you need.

---

## How to Enable CRUD

### Step 1: Add the Code
To enable CRUD in your app, add this line to the `out` method of your Python file:

```python
return self.ins._apps._crud(properties=self.app._properties)
```

### Step 2: Connect to `properties.json`
This code links your app to a file called `properties.json`. This file controls how your data is displayed, edited, and filtered.

### What Happens Next?
Your app will now have:
- A list of items.
- Buttons to add, edit, or delete items.
- Filters to search and sort items.

---

## Customizing CRUD with `properties.json`

### What is `properties.json`?
This file lets you customize how your CRUD system works. You can decide:
- What data to show in the list.
- What fields to include in forms.
- How to filter the data.

### Key Parts of `properties.json`

#### 1. Choose a Table
Tell the CRUD system which database table to use:
```json
"table": "kit_menu"
```

#### 2. Customize the List View
Decide which fields to show in the list:
```json
"list_data": [
    {
        "name": "title",
        "title": "Title",
        "view": "text",
        "class": "ins-col-grow"
    },
    {
        "name": "status",
        "title": "Status",
        "view": "text",
        "class": "ins-col-2"
    }
]
```
- **`name`**: The database field name.
- **`title`**: The label to display.
- **`view`**: How the field looks (e.g., text).
- **`class`**: CSS styling for layout.

#### 3. Create a Form
Define the fields for adding or editing items:
```json
"form_data": [
    {
        "name": "title",
        "title": "Title *",
        "_type": "input",
        "type": "text",
        "required": true,
        "pclass": "ins-col-6"
    }
]
```
- **`_type`**: The input type (e.g., text box).
- **`required`**: Makes the field mandatory.

#### 4. Add Filters
Set up filters to search or sort data:
```json
"list_filter": [
    {
        "name": "title",
        "title": "Search Title",
        "_type": "input",
        "type": "text",
        "_info": "Search in <b>Title</b> by <b>@(value)</b>",
        "main": true,
        "pclass": "ins-col-12"
    }
]
```
- **`_info`**: Custom search information text.
- **`main`**: By enabling this field, the filter will appear on the main page (at the top of the list page).

---

## Dynamic CRUD Setup in Python

### Skip the JSON File
If you don’t want to use `properties.json`, you can define CRUD options directly in Python.

#### Example:
```python
ops = self.ins._apps._crud_ops

# List fields
ops._list_data = [
    {"name": "title", "title": "Title", "view": "text", "class": "ins-col-9"}
]

# Form fields
ops._form_data = [
    {"name": "title", "title": "Title", "_type": "input", "type": "text"}
]

# Filters
ops._list_filter = [
    {"name": "title", "title": "Search Title", "_type": "input", "type": "text"}
]

# Table name
ops._table = "kit_menu"

# Return CRUD system
return self.ins._apps._crud(ops)
```

---

## Why Use `properties.json`?

Using `properties.json` makes it easy to:
- Update settings without changing code.
- Test changes instantly by saving the file.
- Work with team members without editing the app’s core logic.

---

This version is designed for beginners with straightforward explanations, examples, and fewer technical details. Let me know if you need further refinements!