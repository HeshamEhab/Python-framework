# Creating and Configuring an Area

## What is an Area?  
An **area** is like a mini-website inside the framework. It has its own structure and components, including apps, widgets, and web files. Think of it as a separate section of your system that can function independently, while still being part of the larger framework.

For example, if your framework is a big house, each area is like a room with its own purpose and design. You can create as many areas as you need, and each can include folders like `ins_apps`, `ins_wdgts`, `ins_web`, and other necessary files to operate as its own mini-website.

---

## How to Create a New Area  

### Step 1: Create the Area Folder  
1. Navigate to the root directory (`home`).  
2. Create a new folder for your area with the prefix `ins`.  
   - **Example:** For an example area, name it `ins_ex` (where `ex` stands for example).  

---

### Step 2: Create an `index.py` File  
1. Inside the newly created area folder, create an `index.py` file.  
2. Add the following code to the `index.py` file:  

```python
from flask import Flask, g, Blueprint, abort, render_template
from ins_kit.ins import ins

area = "ins_ex"  # Replace with your area name
tmp = f"../{area}/{ins._map.WEB_FOLDER}/{ins._map.TEMPLATES_FOLDER}"
static = f"../{area}/{ins._map.WEB_FOLDER}"

ins_ex_bp = Blueprint(area, __name__, template_folder=tmp, static_folder=static)

@ins_ex_bp.route('/', defaults={'path': ''}, methods=['GET', 'POST'])
@ins_ex_bp.route('/<path:path>', methods=['GET', 'POST'])
def admin(path):
    return ins._tmp._render(area, path)
```

#### Notes:  
- If the area needs to be secured (e.g., an admin panel), replace the last return statement with:  
  ```python
  return ins._tmp._login(area, path)
  ```  
- If the area should be publicly accessible (e.g., a homepage), keep:  
  ```python
  return ins._tmp._render(area, path)
  ```

---

### Step 3: Add the Area to `app.json`  
1. Open the file located at `/ins_pros/app.json`.  
2. Under the `"areas"` tag, add an entry for your area:  

```json
"ins_ex": { 
    "url": "ins_ex",
    "name": "ins_ex",
    "title": "Ex Area", 
    "logo": "ex.png" 
}
```

#### Key Points:  
- **Key and Name and URL:** Should match exactly; these identify the area in the system.  
- **Title:** Displayed as the area's title in the UI.  
- **Logo:** Path to the logo file for the area.  

---

### Step 4: Register the Area in the Main File  
1. Open the main file that starts the system.  
2. Add the following in the `include` section:  
   ```python
   from ins_ex.index import ins_ex_bp
   ```  
3. Before the `app.run` method, register the area with a URL prefix:  
   ```python
   app.register_blueprint(ins_ex_bp, url_prefix=f"/ins_ex")
   ```
   
**The code after adding this two lines should be like this**
    
        from flask import Flask, request
        from ins_kit.ins import ins
        from index import ahome
        from ins_admin.index import ins_admin_bp
        from ins_ex.index import ins_ex_bp ##import new area
        from ajax import ajax_bp

        app = Flask(__name__)

        app.secret_key = 'ins12345'
        app.config['SESSION_TYPE'] = 'filesystem'
        @app.before_request
        def before_request():
        ins._eng._int(request.path)

        app.register_blueprint(ahome, url_prefix=f"/")

        app.register_blueprint(ins_admin_bp, url_prefix=f"/ins_admin")

        app.register_blueprint(ins_ex_bp, url_prefix=f"/ins_ex") ##register new area

        app.register_blueprint(ajax_bp, url_prefix=f"/ins_ajax")

        if __name__ == '__main__':
         app.run(debug=True)

---

### Step 5: Define a UI Template  
1. Access the admin panel:  
   - Navigate to `Settings -> Database`.  
   - Open the `kit_template` table.  
2. If you haven’t created a specific template for your new area, you can duplicate an existing one.  
   - **Example:** Duplicate the `ins_admin` template row.  
   - Replace the `tar_area` field value with the new area name (`ins_ex`).  
   - Ensure the `kit_default` field value is set to `1`.

---

### Step 6: Create an App for the Area  
1. Inside the area folder, create a subfolder for apps named `ins_apps`.  
2. Follow the [App Creation Guide](/Python-framework/app) to create an app within this folder.  

---

### Step 7: Add a Menu Item  
1. Refer to the [Menu Item Creation Guide](/Python-framework/menu_item) to link the app to the area’s menu.  

---

## Accessing the Area  
1. Enter your area’s name in the URL:  
   - **Example:** `https://insya.ins_ex.com`  
2. If the area is secured (`ins._tmp._login`), you must log in to access it.  

---

## Notes:  
- **Folder Structure:** Ensure all necessary folders (e.g., `ins_apps`, `ins_web`) exist within the area, even if not initially used.  
- **Flexibility:** Areas can be structured to include any required part of the framework.
