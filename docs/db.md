## Database Management from Admin Panel

You can manage all database operations from the **admin panel**. From the **admin side panel**, click on **Settings** and then click on **Database**. You can:

- Insert tables or rows
- Edit table structures or individual rows
- View table data
- Remove tables or rows

---

### 1. Managing Tables

#### How to Add a New Table

1. Click on the **(+ Add Table)** button.
2. The SQL area will be filled with the following default SQL structure:

```sql
CREATE TABLE `$table_name` (
 `id` int(11) NOT NULL,
 `title` varchar(255) NOT NULL,
 `des` text DEFAULT NULL,
 `kit_deleted` tinyint(4) NOT NULL DEFAULT 0,
 `kit_disabled` tinyint(4) NOT NULL DEFAULT 0,
 `kit_modified` datetime NOT NULL,
 `kit_created` datetime NOT NULL
) ENGINE=MyISAM DEFAULT CHARSET=utf8mb4 COLLATE=utf8mb4_general_ci;

ALTER TABLE `$table_name` ADD PRIMARY KEY (`id`);
ALTER TABLE `$table_name` MODIFY `id` int(11) NOT NULL AUTO_INCREMENT; 
COMMIT;
```

3. Replace the variable `$table_name` with your table name. Be careful! You need to replace it **in three places**.
4. Auto-generated fields like these **must always be included** in your table:
   - `id`
   - `kit_deleted`
   - `kit_disabled`
   - `kit_modified`
   - `kit_created`

   > Other fields can be edited or removed based on your requirements.

5. You can learn more about MySQL database field types [here](#).
6. After completing your SQL, click on the **(Run)** button to create the table.
7. The newly created table will appear at the **top of the table list**.


---

#### How to Update Table Structure

1. To update a table structure, click on the <i class="fas fa-cog" style='color:blue;'></i> in the table row.
2. This will take you to a page displaying all fields and their types as rows.
3. You can:
   - **Edit** existing fields.
   - **Add a new field** by clicking on the **(+ Add Field)** button.

4. When adding a new field:
   - The SQL area will automatically be filled with SQL for adding a field.
   - Replace the variable `$column_name` with your field name.
   - Change the field type if necessary (default is `varchar(255)`).

   Example SQL:
   ```sql
   ALTER TABLE `your_table_name` ADD `$column_name` varchar(255);
   ```

5. Click on the **(Run)** button, and the new field will appear in the field list.


<iframe src="https://drive.google.com/file/d/1FeABIfZbJIwOe-fwMgcOZ73z7zq4VC9q/preview" width="640" height="480" allow="autoplay"></iframe>

---

### 2. Managing Table Data

To access the data inside a table:

1. Click on the <i class="fa-solid fa-arrow-right" style='color:blue;'></i> in the table row.
2. This will lead you to the **data view** for that table.

Each row represents a record in the table. You can:

#### Add a New Row

1. Click on the **(+ Insert)** button.
2. The SQL area will be filled with SQL for inserting a row:

   ```sql
   INSERT INTO `your_table_name` (`field1`, `field2`, ...) VALUES ('$field1_val', '$field2_val', ...);
   ```

3. Replace the variables with the values you want to insert:
   - `id` is **auto-incremented**.
   - `kit_deleted` and `kit_disabled` are **0 by default**.
   - `kit_created` and `kit_modified` default to the **current date and time**.

   Example:
   ```sql
   INSERT INTO `my_table` (`title`, `des`) VALUES ('My Title', 'Some Description');
   ```

4. Click on the **(Run)** button to add the record.

---

#### Update or Delete a Row

- **Edit**: Click on the <i class='fas fa-pen' style='color:blue;'></i>  next to the record. The SQL area will be filled with an `UPDATE` statement:
   ```sql
   UPDATE `your_table_name` SET `field_name` = 'new_value' WHERE `id` = record_id;
   ```
- **Delete**: Click on the <i class='fas fa-close' style='color:red;'></i>  to delete the record.

<iframe src="https://drive.google.com/file/d/1P68vgjK7ErOWgkfVzKbue9x9JJAYQvnI/preview" width="640" height="480" allow="autoplay"></iframe>

---

### 3. Table Actions

In the table list, you will find additional actions:

1. **Empty Table**: Click on the  <i class='fas fa-crop' style='color:red;' style='color:red;'></i>   to **clear all data** in the table without removing its structure.
2. **Delete Table**: Click on the <i class='fas fa-close' style='color:red;'></i>  to remove the table completely.

---

### Summary
With the admin panel's database tools, you can easily:

- Create tables and define their structure.
- Add, edit, or delete fields.
- Insert, update, or delete records.
- Manage tables without writing complex SQL manually.

These features ensure efficient management of your application's database while minimizing the risk of errors.

