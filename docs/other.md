# Custom Options in CRUD Input Configuration

This guide explains some helpful options you can use to control how `<select>` inputs work in your CRUD system.

---

## `fl_data`

Use this when you want to manually define the options for a `<select>` input (instead of pulling from the database).

**Example:**
```json
"fl_data": {
  "value": "data",
  "value_2": "data_2"
}
This will create a select box with two options:

Option 1: value = "value", display text = "data"

Option 2: value = "value_2", display text = "data_2"

fl_start
Use this to add a default or placeholder option at the top of the select dropdown.

Example:

"fl_start": "0,\"-\""
This will add an option at the top of the select:

value = 0, display text = "-"

Useful when you're fetching options from the database but still want a “Select…” or blank option first.

fl_where
Use this when the <select> is pulling data from the database and you want to apply a custom WHERE clause to filter the results.

Example:

"fl_where": "`fk_users_id` = '3'"`
This will limit the fetched data to entries where fk_users_id equals 3.

list_where
Use this in the page properties to apply a general WHERE clause for the data shown in the main list view (CRUD table).

Example:

"list_where": "`status` = 'active'"`
Only rows with status = 'active' will be shown in the table.

list_query
Use this to write your own full SQL query for fetching the list view data. This overrides the default system query.

Example:

"list_query": "SELECT * FROM users WHERE role = 'admin'"
This will replace the default list query and use your custom one instead.

Summary Table
Option	Purpose
fl_data	Manually set select input options
fl_start	Add a default/placeholder option at the top
fl_where	Add a custom WHERE clause when fetching select data
list_where	Filter list view data globally
list_query	Override the full SQL query for list data