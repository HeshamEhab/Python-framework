# What is a Widget?

a **widget** is a reusable **UI (User Interface)** component or module that performs a specific function or displays a specific part of the content on a website or application. Widgets are often used to simplify the structure of code and allow developers to reuse them in different parts of a project.

Think of a widget as a small, self-contained building block for your website. For example:
- **Header Widget:** Displays the header of your site, including a logo, navigation menu, etc.
- **Footer Widget:** Displays the footer of your site, including copyright information and links.
- **Sidebar Widget:** Displays additional information, such as related articles or ads.

Widgets help break down a website into smaller parts, making it easier to maintain, update, and reuse code.
# How to Create a Widget

Widgets in this system can be created in two ways: by adding static content or by creating new widgets from folders. Follow the steps below based on your needs.

## Scenario 1: Add Static Content to a Widget

### Step 1: Add Content

1. Go to the **Admin Panel**.
2. From the side panel, select **Content** > **Content Menu Item**.
3. A list of all content will appear. Click **Add** to create new content.
4. Fill in the following fields:
   - **Content Title**: A title for internal use (not visible in the content body).
   - **Content**: Add simple text or HTML.
5. Click **Save** and note the **ID** shown in the URL (you will need this later).

### Step 2: Add Content to a Widget

1. From the side panel, select **Settings** > **Widgets**.
2. A list of existing widgets will appear. Click **Add** to create a new widget.
3. Fill in the following fields:
   - **Widget Title**: A name for internal use (visible to users).
   - **Source Section**: Choose the area (e.g., Home, Admin) where the widget will be used.
   - **Content ID**: After selecting the area and "Content," enter the ID of the content you created.
   - **Position**: Specify the widget's position on the screen (e.g., Header, Footer).
   - **Class**: Optionally, add framework classes (e.g., `ins-col ins-card ins-padding ins-font`).
4. Click **Save** to create the widget.

## Scenario 2: Add a New Widget from Folders

### Step 1: Create the Widget Folder and File

1. Decide the area for the widget (e.g., Home, Admin).
2. In the selected area's folder, navigate to `ins_wdgts`.
3. Create a new folder named `wdg_<widget_name>` (e.g., `wdg_mywidget`).
4. Inside this folder, create a Python file with the same name as the folder, using camelCase (e.g., `myWidget.py`).

### Step 2: Add Additional Files and Properties (Optional)

- **Properties**: Create a `properties.json` file to define widget options. Example:
  ```json
  {
      "options": [{
          "_type": "input",
          "title": "Content",
          "name": "id"
      }]
  }
  ```
  - When creating the widget in the admin portal, these fields will appear under the "Properties" section.
  - Use these values in code: `self.widget._options["id"]`.
- **JS and CSS**:
  - Navigate to the `ins_web` folder in the same area.
  - Create a folder with the same name as your widget folder (e.g., `wdg_mywidget`).
  - Add files like `script.js` and `style.css`.
  - Include them in your Python file:
    ```python
    self.widget._include("script.js")
    self.widget._include("style.css")
    ```

### Step 3: Add the Widget in the Admin Portal

1. From the side panel, select **Settings** > **Widgets**.
2. A list of existing widgets will appear. Click **Add** to create a new widget.
3. Fill in the following fields:
   - **Widget Title**: A name for internal use (visible to users).
   - **Source Section**: Choose the area where the widget is located.
   - **Widget**: Select the newly created widget.
   - **Properties**: If properties were defined in `properties.json`, their fields will appear here.
   - **Position**: Specify the widget's position on the screen (e.g., Header, Footer).
   - **Class**: Optionally, add framework classes (e.g., `ins-col ins-card ins-padding ins-font`).
4. Click **Save** to add the widget.

## Notes

- Use meaningful titles for both content and widgets to make management easier.
- Always follow the naming conventions for folders, files, and classes to ensure the system recognizes your widget.
- Test the widget in its intended position to verify its appearance and functionality.

By following these steps, you can easily create and manage widgets in the system!

