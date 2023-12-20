# AIRA Form (Functions)

Make form handling a breeze with AIRA's JavaScript functions. These user-friendly tools help you customize forms effortlessly, ensuring seamless user experiences and efficient data processing.

## 1. getElement : 
Retrieves and returns a jQuery object representing the specified HTML element or elements identified by eleName.

### Syntax
```js
getElement(eleName)
```
### Parameter

| Parameter Name | Description                                                       |
| ---------------| ----------------------------------------------------------------- |
| eleName        |  The identifier or selector for the target element or elements.   |

### Explanation:

* The getElement function is designed to encapsulate an HTML element or a collection of elements within a jQuery object, allowing developers to leverage jQuery methods and utilities for enhanced manipulation and interaction.
* It accepts a single parameter, eleName, which is a string representing the identifier or selector of the target element or elements.
* The returned jQuery object provides a convenient interface for performing operations like DOM manipulation, event handling, and animation on the selected element(s).
* This function bridges the gap between traditional JavaScript and jQuery, enabling developers to utilize jQuery features selectively within their applications.

### Usage:

Developers can call this function with the identifier or selector of the desired HTML element to obtain a jQuery object representing that element.

### Calling Examples 

#### By User Name
```js
let _element = getElement('input[name="data[email]"]');
console.log("element is : ", _element);
```
#### By ID
```js
let _element = getElement('#emailInput');
console.log("element is : ", _element);
```
#### By Class Name
```js
let _element = getElement('.form-control);
console.log("element is : ", _element);
```
### Example Output
```js
Jquery Object -
{
    "length": 0,
    "prevObject": {
        "0": {
            "location": {
                "ancestorOrigins": {},
                "href": "http://localhost:3000/app/cases",
                "origin": "http://localhost:3000",
                "protocol": "http:",
                "host": "localhost:3000",
                "hostname": "localhost",
                "port": "3000",
                "pathname": "/app/cases",
                "search": "",
                "hash": ""
            },
            "__reactEvents$c60powbs52k": {}
        },
        "length": 1
    }
}
```
*****
## 2. getElementValue : 

Retrieves and returns the current value of the specified HTML element or form field identified by eleName.

### Syntax

```js
getElementValue(eleName)
```
### Parameter

| Parameter Name      | Description                                                                   |
| ------------------- | ----------------------------------------------------------------------------- |
| eleName             | The identifier or selector for the target element or form field.              |

### Explanation:

* The getElementValue function is designed to provide a straightforward way to obtain the current value of an HTML element or form field in a web page.
* It accepts a single parameter, eleName, which is a string representing the identifier or selector of the target element.
* This function is particularly useful when developers need to retrieve user inputs from form fields, such as textboxes, dropdowns, checkboxes, or radio buttons.
* The returned value can be utilized for validation, further processing, or manipulation within JavaScript applications.

### Usage:

Developers can call this function with the identifier or selector of the desired HTML element to obtain its current value.

### Calling Examples

![1](https://github.com/airacommunity/ARIA-Documentation/assets/153823636/19350265-82a0-4447-888f-7b41f42b8514)

```js
<input class="form-control" type="email" name="data[email]" id="emailInput" value=" john@aira" >
```
#### By Field  Name

```js
let _element = getElementValue('input[name="data[email]"]');
console.log("element value is: ", _element);
```

#### By Id
```js
let _element = getElementValue('#emailInput');
console.log("element value is: ", _element);
```

#### By Class Name
```js
let _element = getElementValue('.form-control);
console.log("element value is: ", _element);
```
### Example Output

```js
element  value is :  john@aira.fr
```
****
## 3. getText : 

Retrieves and returns the text content of the specified HTML element identified by eleName.

### Syntax

```js
getText(eleName)
```
### Parameter

| Parameter Name      | Description                                                                   |
| ------------------- | ----------------------------------------------------------------------------- |
| eleName             | The identifier or selector for the target element.                            |

### Explanation:

* The getText function is designed to fetch and provide the textual content of a specific HTML element in a web page.
* It accepts a single parameter, eleName, which is a string representing the identifier or selector of the target element.
* This function is particularly useful when developers need to extract text from elements such as paragraphs, headings, or any other container element.
* The returned text content can be used for displaying information, processing, or further manipulation within JavaScript applications.

### Usage:

Developers can call this function with the identifier or selector of the desired HTML element to obtain its text content.

### Calling Examples

```js
<input class="form-control" type="email" name="data[email]" id="emailInput" value=" john@aira.fr" >
```
#### By Field Name

```js
let _element = getText('input[name="data[email]"]');
console.log("element text is: ", _element);
```

#### By Id
```js
let _element = getText('#emailInput');
console.log("element text is: ", _element);
```

#### By Class Name
```js
let _element = getText('.form-control);
console.log("element text is: ", _element);
```
### Example Output

```js
element  text  is :  john@aira.fr
```

#### Note

| Options             | Description                                                                   |
| ------------------- | ----------------------------------------------------------------------------- |
| Dropdown boxes and Radio buttons| It returns the displayed text of the field's selected option.     |
|Checkboxes|It returns the text label of the marked or unmarked option. |
||If this text label hasn't been configured, then by default,| 
||a marked checkbox is "true" and an unmarked checkbox is "false"|
|Textboxes, Textareas, Suggest and Hidden fields|It returns the value of the field.|
*****
## 4. getElementAttrValue : 

Retrieves and returns the value of the specified attribute (attrName) of the HTML element identified by eleName.

### Syntax

```js
getElementAttrValue(eleName, attrName)
```
### Parameter

| Parameter Name      | Description                                                                   |
| ------------------- | ----------------------------------------------------------------------------- |
|   eleName           |    The identifier or selector for the target element.                         |   
|   attrName          |   The name of the attribute whose value is to be retrieved.                   |   

### Explanation:

* The getElementAttrValue function is designed to obtain the value of a specific attribute (attrName) from a given HTML element.
* It accepts two parameters: eleName (the identifier or selector of the target element) and attrName (the name of the attribute).
* This function is particularly useful when developers need to retrieve specific attribute values, such as the src attribute of an image or the href attribute of a link.
* The returned attribute value can be utilized for various purposes, including dynamic content loading or hyperlink navigation.

### Usage:

Developers can call this function with the identifier or selector of the desired HTML element and the name of the target attribute to obtain its value.

### Calling Examples

```js
<img classname="imgClass" id=”imgId” href="abc.com" />
```
#### By Id
```js
let _element = getElementAttrValue(".imgClass", "href");
console.log("element attr is: ", _element);
```

#### By Class Name
```js
let _element = getElementAttrValue("#imgID", "href");
console.log("element attr is: ", _element);
```
### Example Output

```js
element  attr  is :  abc.com
```
*****
## 5.setFieldValue : 

Updates the value of the specified form field identified by fieldName with the provided fieldValue.
### Syntax

```js
setFieldValue(fieldName, fieldValue)
```
### Parameter

| Parameter Name      | Description                                                                   |
| ------------------- | ----------------------------------------------------------------------------- |
| fieldName | The identifier or selector for the target form field.| 
| fieldValue | The new value to be set for the specified form field.|

### Explanation:

* The setFieldValue function is designed to modify the value of a specific form field identified by fieldName.
* It accepts two parameters: fieldName (the identifier or selector of the target form field) and fieldValue (the new value to be assigned to the field).
* This function is particularly useful when developers need to programmatically update the content of input fields, text areas, or other user-input elements in a form.
* The field value is set to the provided fieldValue, allowing dynamic manipulation of form data.

### Usage:

Developers can call this function with the identifier or selector of the desired form field and the new value to update it.

### Calling Examples

```js
<input class="form-control" type="email" name="email id="emailInput" >
```
#### By Feild Name
```js
let _element = setFieldValue('email','john@aira.fr');
```
*****

## 6. setText : 

Updates the default text value of the specified form field identified by fieldName with the provided fieldValue.
### Syntax

```js
setText(fieldName, fieldValue)
```
### Parameter

| Parameter Name      | Description                                                                   |
| ------------------- | ----------------------------------------------------------------------------- |
| fieldName | The identifier or selector for the target form field. |
| fieldValue | The new default text value to be set for the specified form field. |

### Explanation:

* The setText function is designed to modify the default text value of a specific form field identified by fieldName.
* It accepts two parameters: fieldName (the identifier or selector of the target form field) and fieldValue (the new default text value to be assigned to the field).
* This function is particularly useful when developers need to provide a default placeholder or initial value for input fields or text areas in a form.
* The default text value is set to the provided fieldValue, allowing for dynamic updates to the default content of form elements.

### Usage:

Developers can call this function with the identifier or selector of the desired form field and the new default text value to update it.

### Calling Examples

```js
<input class="form-control" type="email" name="email id="emailInput" >
```
#### By Feild Name
```js
let _element = setText('email','john@aira.fr');
```
#### Note:
| Options             | Description                                                                   |
| ------------------- | ----------------------------------------------------------------------------- |
| Dropdown|Set the 'selected option'. This parameter must be one of the options already defined in the control.|
||If the parameter does not exist in the dropdown's options, the dropdown will be displayed with its first option selected.|
|Checkboxes|Set to the text label of the marked or unmarked option. Alternatively, to mark or unmark a checkbox, |
||set its text as same as its text label in the "options" property. If this text label hasn't been configured, |
||then by default, a marked checkbox is "true" and an unmarked checkbox is "false".|
|Textboxes, textareas, suggest boxes and hidden controls|Set the new value of the field.|

*****

## 7. setLabel : 

Updates the label of the specified form field identified by fieldName with the provided fieldValue.
### Syntax

```js
setLabel(fieldName, fieldValue)
```
### Parameter

| Parameter Name      | Description                                                                   |
| ------------------- | ----------------------------------------------------------------------------- |
| fieldName | The identifier or selector for the target form field.|
| fieldValue | The new label text to be set for the specified form field.|

### Explanation:

* The setLabel function is designed to modify the label text associated with a specific form field identified by fieldName.
* It accepts two parameters: fieldName (the identifier or selector of the target form field) and fieldValue (the new label text to be assigned to the field).
* This function is particularly useful when developers need to dynamically update the label text of a form field, providing improved accessibility or reflecting changes in the user interface.
* The label text is set to the provided fieldValue, allowing for dynamic updates to the content of form field labels.

### Calling Examples

```js
<input class="form-control" type="email" name="email” id="emailInput" >
```
#### By Feild Name
```js
let _element = setLabel('email','john@aira.fr');
```
*****

## 8. hideElement : 

Hides the specified HTML element identified by eleName from the user interface.

### Syntax

```js
hideElement(eleName)
```
### Parameter

| Parameter Name      | Description                                                                   |
| ------------------- | ----------------------------------------------------------------------------- |
| eleName | The identifier or selector for the target element to be hidden. |

### Explanation:

* The hideElement function is designed to make a specified HTML element invisible on the user interface.
* It accepts a single parameter, eleName, which is a string representing the identifier or selector of the target element.
* This function is particularly useful when developers need to dynamically control the visibility of elements based on certain conditions or user interactions.
* The targeted element is hidden from view, effectively removing it from the user's screen.

### Usage:

Developers can call this function with the identifier or selector of the desired HTML element to hide it.

### Calling Examples

```js
<input class="form-control" type="email" name="data[email]” id="emailInput" >
```
#### By Field  Name

```js
let _element = hideElement('input[name="data[email]"]');
```

#### By Id
```js
let _element = hideElement('#emailInput');
```

#### By Class Name
```js
let _element = hideElement('.form-control);
```
*****

## 9. showElement : 

Displays the specified HTML element identified by eleName on the user interface if it is currently hidden.
### Syntax

```js
showElement(eleName)
```
### Parameter

| Parameter Name      | Description                                                                   |
| ------------------- | ----------------------------------------------------------------------------- |
| eleName | The identifier or selector for the target element to be shown. |

### Explanation:

* The showElement function is designed to make a specified HTML element visible on the user interface if it is currently hidden.
* It accepts a single parameter, eleName, which is a string representing the identifier or selector of the target element.
* This function is particularly useful when developers need to dynamically control the visibility of elements based on certain conditions or user interactions.
* If the targeted element is hidden, this function makes it visible, allowing it to be displayed to the user.

### Usage:

Developers can call this function with the identifier or selector of the desired HTML element to show it.

### Calling Examples

```js
<input class="form-control" type="email" name="data[email]” id="emailInput" hidden >
```
#### By Field  Name

```js
let _element = showElement('input[name="data[email]"]');
```

#### By Id
```js
let _element = showElement('#emailInput');
```

#### By Class Name
```js
let _element = showElement('.form-control);
```
*****

## 10. getGridValues : 

Retrieves and returns the data values of the specified grid identified by gridName.

### Syntax

```js
getGridValues(gridName)
```
### Parameter

| Parameter Name      | Description                                                                   |
| ------------------- | ----------------------------------------------------------------------------- |
| gridName | The identifier or selector for the target grid. |

### Explanation:

* The getGridValues function is designed to obtain an array of data values from a specified grid on the user interface.
* It accepts a single parameter, gridName, which is a string representing the identifier or selector of the target grid.
* This function is particularly useful when developers need to access the data within a grid for further processing, analysis, or presentation.
* The returned array contains the data values from the specified grid.

### Usage:

Developers can call this function with the identifier or selector of the desired grid to obtain its data values.

### Calling Examples

#### By Field  Name

```js
let _element = getGridValues('datagrid');
```
*****

## 11. setGridDataValue : 

Updates the data of the specified grid identified by gridName with the provided gridValues. The addNew parameter determines whether to add a new row or replace existing data.

### Syntax

```js
setGridDataValue(gridName, gridValues, addNew)
```
### Parameter

| Parameter Name      | Description                                                                   |
| ------------------- | ----------------------------------------------------------------------------- |
| gridName | The identifier or selector for the target grid.|
| gridValues | The array of data values to be set for the specified grid.|
| addNew | Determines whether to add a new row (true) or replace existing data (false).|

### Explanation:

* The setGridDataValue function allows developers to dynamically update the data of a specified grid on the user interface.
* It accepts three parameters:
   * gridName: The identifier or selector of the target grid.
   * gridValues: An array of data values to be set for the grid.
   * addNew: A boolean flag indicating whether to add a new row (true) or replace existing data (false).
* This function is particularly useful when developers need to update or modify the data displayed within a grid based on user interactions or other application logic.

### Usage:

Developers can call this function with the identifier or selector of the desired grid, an array of new data values, and a boolean flag indicating whether to add a new row or replace existing data.

### Calling Examples

#### By Field  Name

```js
let _element = setGridDataValue('datagrid',[{name:”shivani”,
age:”26”,email:”shivani@aira.fr”}],false);
```
*****

## 12. getNoOfRows : 

Returns the number of rows in the specified grid identified by gridName.

### Syntax

```js
getNoOfRows(gridName)
```
### Parameter

| Parameter Name      | Description                                                                   |
| ------------------- | ----------------------------------------------------------------------------- |
| gridName | The identifier or selector for the target grid. |

### Explanation:

* The getNoOfRows function is designed to provide the count of rows in a specified grid on the user interface.
* It accepts a single parameter, gridName, which is a string representing the identifier or selector of the target grid.
* This function is particularly useful when developers need to determine the size or length of the data set within a grid.
* The returned value represents the number of rows in the specified grid.

### Usage:

Developers can call this function with the identifier or selector of the desired grid to obtain the number of rows.

### calling Example

| Name     |Age                   |       Email                                     |
| ------------------- | ----------------------------------------------------------------------------- |
| Shivani |26 | shivani@aira.fr   |

#### By Field Name
```js
let _element = getNoOfRows('datagrid');
console.log("element : ", _element);;
```
### Example Output
```js
element  attr  is :  1
```
*****

## 13. getGridHeader : 

Returns an array of table header values from the specified grid identified by gridName.

### Syntax

```js
getGridHeader(gridName)
```
### Parameter

| Parameter Name      | Description                                                                   |
| ------------------- | ----------------------------------------------------------------------------- |
| gridName | The identifier or selector for the target grid. |

### Explanation:

* The getGridHeader function is designed to obtain an array of header values from the table header of a specified grid on the user interface.
* It accepts a single parameter, gridName, which is a string representing the identifier or selector of the target grid.
* This function is particularly useful when developers need to retrieve the column headers of a grid for display, configuration, or further processing.
* The returned array contains the header values of the specified grid.

### Usage:

Developers can call this function with the identifier or selector of the desired grid to obtain its table header values.

### calling Example

| Name     |Age                   |       Email                                     |
| ------------------- | ----------------------------------------------------------------------------- |
| Shivani |26 | shivani@aira.fr   |

![2](https://github.com/airacommunity/ARIA-Documentation/assets/153823636/01a3d4d5-c27b-4fdf-9e34-e940b6b64395)


#### By Field Name
```js
let _element = getGridHeader(".formio-component-dataGrid", 0, 1)
console.log("output is : ", _element);
```
### Example Output
```js
 [
    "Name",
    "Age",
    "Email",
    "Add/Remove"
]

```
*****

## 14. getGridValue : 

Returns the value of a specific table cell in the specified grid identified by gridName, based on the specified row and column indices.

### Syntax

```js
getGridValue(gridName, row, column)
```
### Parameter

| Parameter Name      | Description                                                                   |
| ------------------- | ----------------------------------------------------------------------------- |
| gridName | The identifier or selector for the target grid. |
| row | The index of the row containing the desired table cell. |
| column | The index of the column containing the desired table cell. |

### Explanation:

* The getGridValue function is designed to retrieve the value of a specific table cell within a grid on the user interface.
* It accepts three parameters:
   * gridName: The identifier or selector of the target grid.
   * row: The index of the row containing the desired table cell.
   * column: The index of the column containing the desired table cell.
* This function is particularly useful when developers need to fetch the content of a specific cell within a grid for further analysis, display, or manipulation.

### Usage:

Developers can call this function with the identifier or selector of the desired grid, along with the row and column indices, to obtain the value of the specified table cell.


### calling Example

| Name     |Age                   |       Email                                     |
| ------------------- | ----------------------------------------------------------------------------- |
| Shivani |26 | shivani@aira.fr   |

![2](https://github.com/airacommunity/ARIA-Documentation/assets/153823636/01a3d4d5-c27b-4fdf-9e34-e940b6b64395)


#### By Field Name
```js
let _element = getGridValue(".formio-component-dataGrid", 0, 1)
console.log("element value is : ", _element);
```
### Example Output
```js
Element value is  :  23
```
*****

## 15. deleteGridRow : 

Deletes the specified row from the table within the grid identified by gridName based on the provided rowInd.

### Syntax

```js
deleteGridRow(gridName, rowInd)
```
### Parameter

| Parameter Name      | Description                                                                   |
| ------------------- | ----------------------------------------------------------------------------- |
| gridName | The identifier or selector for the target grid. |
| rowInd | The index of the row to be deleted from the table within the grid. |

### Explanation:

* The deleteGridRow function is designed to remove a specific row from the table within the specified grid on the user interface.
* It accepts two parameters:
   * gridName: The identifier or selector of the target grid.
   * rowInd: The index of the row to be deleted from the table within the grid.
* This function is particularly useful when developers need to dynamically remove rows from a grid based on user interactions or specific application logic.

### Usage:

Developers can call this function with the identifier or selector of the desired grid and the index of the row to be deleted.

******
## 16. addGridRow : 

Adds a new row at the beginning of the table within the grid identified by gridName.

### Syntax

```js
addGridRow(gridName)
```
### Parameter

| Parameter Name      | Description                                                                   |
| ------------------- | ----------------------------------------------------------------------------- |
| gridName | The identifier or selector for the target grid. |

Explanation:

* The addGridRow function is designed to insert a new row at the beginning of the table within the specified grid on the user interface.
* It accepts a single parameter:
   * gridName: The identifier or selector of the target grid.
* This function is particularly useful when developers need to dynamically add rows to a grid, for example, when inserting new data or allowing users to input information.

### Usage:

Developers can call this function with the identifier or selector of the desired grid to add a new row at the beginning of the table.

*****

## 17. hideColumn : 

Hides the specified column in the table within the grid identified by gridName based on the provided columnInd.

### Syntax

```js
hideColumn(gridName,columnInd)
```
### Parameter

| Parameter Name      | Description                                                                   |
| ------------------- | ----------------------------------------------------------------------------- |
| gridName | The identifier or selector for the target grid. |
| columnInd | The index of the column to be hidden in the table within the grid. |

### Explanation:

* The hideColumn function is designed to make a specific column invisible within the table of the specified grid on the user interface.
* It accepts two parameters:
  * gridName: The identifier or selector of the target grid.
  * columnInd: The index of the column to be hidden in the table within the grid.
* This function is particularly useful when developers need to dynamically control the visibility of columns based on user interactions or specific application requirements.

### Usage:

Developers can call this function with the identifier or selector of the desired grid and the index of the column to be hidden.

*****

## 18. showColumn : 

Shows the specified hidden column in the table within the grid identified by gridName based on the provided columnInd.

### Syntax

```js
showColumn(gridName,columnInd)
```
### Parameter

| Parameter Name      | Description                                                                   |
| ------------------- | ----------------------------------------------------------------------------- |
| gridName | The identifier or selector for the target grid. |
| columnInd | The index of the hidden column to be shown in the table within the grid. |

### Explanation:

* The showColumn function is designed to make a specific hidden column visible within the table of the specified grid on the user interface.
* It accepts two parameters:
  * gridName: The identifier or selector of the target grid.
  * columnInd: The index of the hidden column to be shown in the table within the grid.
* This function is particularly useful when developers need to dynamically control the visibility of columns based on user interactions or specific application requirements.

### Usage:

Developers can call this function with the identifier or selector of the desired grid and the index of the hidden column to be shown.


*****

## 19. getGridData : 

Retrieves and returns the complete data set (rows and columns) from the table within the grid identified by gridName.

### Syntax

```js
getGridData(gridName)
```
### Parameter

| Parameter Name      | Description                                                                   |
| ------------------- | ----------------------------------------------------------------------------- |
| gridName | The identifier or selector for the target grid. |

### Explanation:

* The getGridData function is designed to provide the entire data set, including all rows and columns, from the table within the specified grid on the user interface.
* It accepts a single parameter:
  * gridName: The identifier or selector of the target grid.
* This function is particularly useful when developers need to obtain the full set of data for further processing, analysis, or storage.

### Usage:

Developers can call this function with the identifier or selector of the desired grid to obtain its complete data set.

### calling Example

| Name     |Age                   |       Email                                     |
| ------------------- | ----------------------------------------------------------------------------- |
| Shivani |26 | shivani@aira.fr   |

![2](https://github.com/airacommunity/ARIA-Documentation/assets/153823636/01a3d4d5-c27b-4fdf-9e34-e940b6b64395)


#### By Field Name
```js
let _element = getGridData(".formio-component-dataGrid")
console.log("output is : ", _element);
```
### Example Output
```js
[
    [
        "Ajay SOni",
        "23",
        "soni.ajay79@aira.fr",
        null
    ]
]
```
*****

## 20. getControl : 

Returns the jQuery object representing the table cell in the specified grid identified by gridName based on the provided row and column indices.

### Syntax

```js
getControl(gridName, rowInd, columnInd)
```
### Parameter

| Parameter Name      | Description                                                                   |
| ------------------- | ----------------------------------------------------------------------------- |
| gridName | The identifier or selector for the target grid. |
| rowInd | The index of the row containing the desired table cell. |
| columnInd | The index of the column containing the desired table cell. |

### Explanation:

* The getControl function is designed to retrieve the jQuery object representing a specific table cell within the grid on the user interface.
* It accepts three parameters:
  * gridName: The identifier or selector of the target grid.
  * rowInd: The index of the row containing the desired table cell.
  * columnInd: The index of the column containing the desired table cell.
* This function is particularly useful when developers need to access and manipulate the properties or contents of a specific cell within a grid using jQuery methods.

### Usage:

Developers can call this function with the identifier or selector of the desired grid, along with the row and column indices, to obtain the jQuery object representing the specified table cell.

### Calling Example

| Name | Count| E-Mail | Add/Remove|
| -----| -----|--------|---------- |
| Shivani | 26 | shivani@aira.fr|➕ ❌|

![2](https://github.com/airacommunity/ARIA-Documentation/assets/153823636/01a3d4d5-c27b-4fdf-9e34-e940b6b64395)

By Element Name
```js
let _element = getControl("dataGrid",0, 1)
console.log("output is : ", _element);
```

### Example Output
```js
Jquery object 
{
    "0": {},
    "length": 1,
    "prevObject": {
        "0": {},
        "length": 1
    }
}

```
*****

## 21. getSummary : 

Returns the summary (e.g., sum or average) of the values in the specified column of the grid identified by gridName.

### Syntax

```js
getSummary(gridName, columnInd)
```
### Parameter

| Parameter Name      | Description                                                                   |
| ------------------- | ----------------------------------------------------------------------------- |
| gridName | The identifier or selector for the target grid. |
| columnInd | The index of the column for which the summary is to be calculated. |

### Explanation:

* The getSummary function is designed to calculate and return the summary (e.g., sum or average) of the values in a specific column within the grid on the user interface.
* It accepts two parameters:
  * gridName: The identifier or selector of the target grid.
  * columnInd: The index of the column for which the summary is to be calculated.
* This function is particularly useful when developers need to obtain aggregate information about a column, such as the total or average of numerical values.

### Usage:

Developers can call this function with the identifier or selector of the desired grid and the index of the column to obtain the summary of its values.

### Calling Example

| Name | Count| E-Mail | Add/Remove|
| -----| -----|--------|---------- |
| Shivani | 26 | shivani@aira.fr|➕ ❌|

#### By Field Name
```js
let _element = getControl(".formio-component-dataGrid",1)
console.log("output is : ", _element);
```

### Example Output
```js
26
```
*****

## 22. disableValidation : 

Disables the validation for the specified input field identified by eleName by setting the "required" attribute to false.

### Syntax

```js
disableValidation(eleName)
```
### Parameter

| Parameter Name      | Description                                                                   |
| ------------------- | ----------------------------------------------------------------------------- |
| eleName | The identifier or selector for the target input field. |

### Explanation:

* The disableValidation function is designed to turn off validation for a specific input field by removing the "required" attribute.
* It accepts a single parameter:
  * eleName: The identifier or selector of the target input field.
* This function is particularly useful when developers need to temporarily or conditionally disable validation for a specific input field, allowing for flexibility in form submission.

### Usage:

Developers can call this function with the identifier or selector of the desired input field to disable its validation.

```
****
Empower your workflow with AIRA - Your Trusted Partner in Automation Solutions. Transform the way you handle forms and enhance user experiences effortlessly. Experience the future of automation with AIRA's intuitive JavaScript functions.
****
****
