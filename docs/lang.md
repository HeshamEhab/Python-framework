# Translation System Documentation

## Introduction
The system supports multiple languages, allowing users to add and manage translations easily. To add a new language, follow the steps below.

---

## Adding a New Language

To add a new language, you need to register it in the `app.json` file located in the `ins_pros` folder. Inside this file, there is an array called `langs` that contains all supported languages.

To add a new language, such as French, add this inside the `langs` array:

```json
"fr": {
    "name": "fr",
    "title": "French",
    "direction": "ltr"
}
```

### Explanation:
- **Key (`fr`)**: The language code used for storing and retrieving data.
- **`name`**: Must match the language key exactly.
- **`title`**: The name that appears in the language selection menu.
- **`direction`**: Defines text direction (`ltr` for left-to-right, `rtl` for right-to-left like Arabic).

---

## Translation Levels

The system has four levels of translations:

### 1. System-Wide Translations
System-wide translations are stored in the `ins_lang` folder, which has subfolders for each language (e.g., `ar`, `en`). Each folder contains JSON files with translations.

#### Default Translation File
By default, a file called `crud.json` exists in each language folder. The system gets translations from this file unless another file is specified.

#### Example:
For the word `save`, add the following:

- In `ar/crud.json`:
  ```json
  "save": "حفظ"
  ```
- In `en/crud.json`:
  ```json
  "save": "Save"
  ```

#### Fetching Translations in Python:
To get a translation in Python:
```python
self.ins._langs._get("save")
```
This gets the word from `crud.json`. To use a different file, specify the file name:
```python
self.ins._langs._get("save", "my_app")
```
Here, `my_app` refers to `my_app.json` inside the language folder.

---

### 2. Application-Specific Translations
Each application can have its own translation files inside its folder. These files must be named with the language code (e.g., `en.json`, `ar.json`).

#### Example:
If `save` exists in the app’s `en.json` and `ar.json`, retrieve it using:
```python
self.app._lang.get("save")
```
This fetches the correct translation based on the system’s current language.

---

### 3. Attribute-Level Translations
You can add multiple language versions for an attribute by appending `-{lang}` to the attribute name. To enable this feature, set `_trans` to `true`.

#### Example:
```json
{
  "_data": "Hello",
  "_data-ar": "اهلا",
  "_data-en": "Hello All",
  "_trans": "true"
}
```
- If the language is Arabic (`ar`), `_data-ar` is used.
- If the language is English (`en`), `_data-en` is used.
- If no specific translation exists, `_data` is used as a fallback.

This works for any attribute, not just `_data`.

---

### 4. User-Defined Translations
Users can enter multilingual data in forms by enabling translation fields. This applies only to specific database fields.

#### Steps to Enable User-Defined Translations:
1. Set `_lang` to `true` in the field options.
2. Specify the database table using `_table`.
3. Ensure the table has a field called `kit_lang`.

#### Example:
```json
{
  "_lang": "true",
  "_table": "kit_menu_item"
}
```
With this setup, users will see a language switcher when entering data, allowing them to input translations for each supported language.

#### Fetching User-Defined Translations:
To get stored translations:
```python
self.ins._db._get_row("kit_menu_item", "*", "id='17'", True)
```
Setting `True` as the last parameter ensures translations are included in the response.

---

## Conclusion
The system provides a flexible translation mechanism with four levels:
- **System-wide translations** for common terms.
- **Application-specific translations** for app content.
- **Attribute-level translations** for UI elements.
- **User-defined translations** for multilingual data entry