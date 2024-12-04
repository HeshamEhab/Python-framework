# Framework Architecture

This document outlines the structure of the system, highlighting its general folders and their purposes. Each folder plays a distinct role in maintaining the modularity and functionality of the framework.

## General Structure

The system contains the following main folders:

### **`ins_apps`**
This folder contains the system's applications. Each app encapsulates a specific functionality or feature of the system.  
[Learn more about `ins_apps` and its usage.](/app)

### **`ins_wdgts`**
This folder contains the system's widgets, reusable components designed to enhance user interface and functionality.  
[Learn more about `ins_wdgts`.](#)

### **`ins_languages`**
This folder stores the system's general language files. Each language is organized into its own subfolder:
- `ar` for Arabic
- `en` for English
- `fr` for French

[Learn more about managing languages.](#)

### **`ins_kits`**
The engine of the system resides in this folder. It contains the core library parts essential for the framework's functionality.  
[Learn more about `ins_kits` and the system's core.](#)

### **`ins_web`**
This folder contains files specific to browser languages, such as JavaScript and CSS.  
To ensure proper linkage, any file in this folder must be located in a path matching the app folder name it belongs to.  
[Learn more about `ins_web`.](#)

## Areas

Areas are self-contained subsystems within the main framework. Each area follows the same folder structure described above and operates independently while contributing to the overall system. For example:

### **`ins_admin`**
The `ins_admin` area includes its own:
- `ins_apps`
- `ins_wdgts`
- `ins_languages`
- `ins_kits`
- `ins_web`

[Learn more about areas like `ins_admin`.](#)

This framework architecture ensures a modular, scalable, and maintainable structure. Click the provided links to explore each part of the system in more detail.

