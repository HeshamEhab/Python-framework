# Creating an App in the System

An **App** is a part of the system that can be used and called from any area. Below are the steps to create an app in the system.

## Steps to Create an App

### 1. Create the App Folder

First, create a folder inside the **`ins_apps`** directory. The folder name should represent your app and be written with prefex `app`.
**Ex**: app_test

### 2. Create the Python File

Inside the app folder, create a Python file with the same name as the folder, followed by the `.py` extension. This file is the minimum requirement to create an app, and it will be enough for the app to work.

- The class name in the Python file should be the same as the folder and file name, written in **CamelCase** (without underscores) in previpus example if app name is `app_test` the class name should be `AppTest`.
- This Python file will initialize the app and make it functional.

### 3. Additional Files (Optional)

You can enhance your app by adding more files:

- **Additional Python Files**: If needed, you can create more Python files for additional functionality.
- **Properties File**: A JSON file called `properties.json` can be created an you can know more about json properties file from [here](/Python-framework/menu_item).
- **JavaScript and CSS Files**: If your app needs JavaScript or CSS, you will need to create a new folder inside the **`ins_web`** directory with the same name as your app. Inside this folder, you can create:
  - `script.js` for JavaScript code.
  - `style.css` for custom styles.

### 4. Make Your App Viewable in the Portal

To make your app accessible and viewable in the portal, you need to follow the instructions provided in this [link](#).

---

This simple structure is all you need to create an app in the system. You can always add more files as required for additional functionality.
