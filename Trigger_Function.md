# Trigger Function


## Triggers In AIRA Workflow

Triggers within the AIRA workflow serve as a mechanism to apply specific business logic based on predefined conditions or events. They play a crucial role in enhancing workflow customization and automation, ensuring that precise actions are executed according to specific requirements.

## Trigger Functions in AIRA

AIRA has developed trigger functions to simplify the process of creating triggers, making it more convenient for users to implement their desired logic within workflows. These trigger functions provide predefined functionalities that can be easily incorporated into triggers, streamlining the trigger creation process and enhancing overall workflow efficiency.

## 1. executeQuery()

The executeQuery function retrieves data from a MySQL database by executing a specified SQL query using the provided MySQL connection ID.

### Syntax:

```
const aira = require("AIRAFunction"); //Load Aira Function

async function getCompanyUser(){
let company_id  = $$company$$; //Global Variables
let sql = "SELECT column1, column2, column3 FROM table_name left join users on users.id = table_name.user_id where column3 = '"+company_id+"'";
let airaObject = new aira(); //Create Aira Class Object
let result = await airaObject.executeQuery(sql, "TGA0SI4MQZZFPWAW5ZL8YCHV5WZTQXQ8"); //Call Execute Query Function with the connection string
//create json object to set data in the current execution
 let data = {
  companyUserId:result[0].column1,
  companyUserEmail:result[0].column2,
  companyUserName: result[0].column2+' '+result[0].column3
}
console.log(JSON.stringify(data)) //Set Output in the current execution
}

getCompanyUser(); //function calling

```
### Parameters

| Parameter | Description |
|------------|-------------|
|query (string) | The SQL query is to be executed against the MySQL database.|
| conn_id (string) | The MySQL connection ID represents the connection to be used for executing the query.|

### Usage:
Ensure that the SQL query is valid and properly formatted according to MySQL syntax. The MySQL connection ID should correspond to a valid connection established within the AIRA workflow environment.


## 2. getCurrentDate()

The getCurrentDate function returns the current date.

### Syntax:

```
const aira = require("AIRAFunction"); //Load Aira Function

async function getCurrentData() {
 let airaObject = new aira(); //Create Aira Class Object
 let result = await airaObject.getCurrentDate(); // Get Current Date
 console.log(JSON.stringify(result)); //Set Output in the current execution
}

getCurrentData(); //function calling

```

### Usage:
Call the getCurrentDate function when you need to retrieve the current date in your program or workflow.

## 3. getCurrentTime()

The getCurrentTime function returns the current time.

### Syntax:

```
const aira = require("AIRAFunction"); //Load Aira Function

async function getCurrentTime() {
 let airaObject = new aira(); //Create Aira Class Object
 let result = await airaObject.getCurrentTime(); // Get Current Time
 console.log(JSON.stringify(result)); //Set Output in the current execution
}

getCurrentTime(); //function calling

```


### Usage:
Call the getCurrentTime function when you need to retrieve the current time in your program or workflow.


## 4. userInformation()

The userInfo function retrieves information about a user with a given ID.

### Syntax:

```
const aira = require("AIRAFunction"); //Load Aira Function

async function userInformation() {
 let airaObject = new aira(); //Create Aira Class Object
 let result = await airaObject.userInfo('00000000000000000000000000000002'); // Get User Details Date
 console.log(JSON.stringify(result)); //Set Output in the current execution
}

userInformation(); //function calling

//get email 
//result[0].email  Output ->  ‘ajay.soni@aira.fr’

userInfo(user_id)
```

### Parameters
| Parameter | Description |
|------------|-------------|
|user_id (string) | The unique ID of the user for whom information is to be retrieved. |

### Usage:
Call the userInfo function with the appropriate user ID to retrieve information about that user.


## 5. groupList()

The groupList function returns a list of groups.
 
### Syntax:
```
const aira = require("AIRAFunction"); //Load Aira Function

async function groupList() {
 let airaObject = new aira(); //Create Aira Class Object

 let result = await airaObject.groupList();
 console.log(JSON.stringify(result)); //Set Output in the current execution
}

groupList(); //function calling

```
### Parameters
| Parameter | Description |
|------------|-------------|
|regex (string, optional) | A string is used to search for specific groups. Defaults to null if not provided. |
|start (integer, optional) | Specifies the starting index from which to retrieve groups. Defaults to null if not provided. |
|limit (integer, optional) | Specifies the maximum number of groups to return. Defaults to null if not provided. |

### Usage:
Call the groupList function with optional parameters to retrieve a list of groups. If no parameters are provided, it returns the entire list of groups.

### Return Value:
An array containing the list of groups, where each element represents a group.


## 6. getGroupUID ():
The `getGroupUID` function retrieves the unique ID of a group based on the group name.

### Syntax:

```
const aira = require("AIRAFunction"); //Load Aira Function

async function groupUid() {
 let airaObject = new aira(); //Create Aira Class Object

 let result = await airaObject.getGroupUID('RU_bouygues'); // Get Groups ID
 console.log(JSON.stringify(result)); //Set Output in the current execution
}

groupUid(); //function calling

//output
//[{"groupId":"X5RPHYJXZFX6YJ9MARAY8KCCKUBIU4NS"}]

```

### Parameters

| Parameter | Description |
|------------|-------------|
|groupName (string) | The name of the group for which the unique ID is to be retrieved. |

### Return Value:

groupUid (string): The unique ID of the group. It
returns false if the group with the provided name does not exist.

### Usage:

Call the getGroupUID function with the group name to retrieve its unique ID. If the group exists, the function returns its unique ID; otherwise, it returns false.


## 7. getGroupName ():
The `getGroupName` function returns the group title of the specified group UID. If the group UID is not found, it returns `false`.

### Syntax:
```
const aira = require("AIRAFunction"); //Load Aira Function

async function findGroupName() {
 let airaObject = new aira(); //Create Aira Class Object

 let result = await airaObject.getGroupName('X5RPHYJXZFX6YJ9MARAY8KCCKUBIU4NS'); // Get Groups Name
 console.log(JSON.stringify(result)); //Set Output in the current execution
}

findGroupName(); //function calling

//output
//[{"name":"RU_bouygues"}]

```

### Parameters

| Parameter | Description |
|------------|-------------|
|groupUid (string) | The ID of the group for which the group title is to be retrieved. |

### Return Value:

A string representing the group title. It
returns false if the specified group UID is not found.

### Usage:

Call the getGroupName function with the group UID to retrieve its group title. If the group UID exists, the function returns its group title; otherwise, it returns false.


## 8. getGroupUsers ():
The `getGroupUsers` function returns the group title of the specified group UID. If the group UID is not found, it returns `false`.

### Syntax:
```
const aira = require("AIRAFunction"); //Load Aira Function

async function getGroupUserDetails() {
 let airaObject = new aira(); //Create Aira Class Object

 let result = await airaObject.getGroupUsers('X5RPHYJXZFX6YJ9MARAY8KCCKUBIU4NS'); // Get Groups User Details 
 console.log(JSON.stringify(result)); //Set Output in the current execution
}

getGroupUserDetails(); //function calling

//output
//[{"id":"145","first_name":"Test10","last_name":"Test10","email":"test10@aira.fr","contact_number":"+911234567890","city":null,"state":null,"country":"IS","group_id":174},{"id":"143","first_name":"Test8","last_name":"Test8","email":"test8@aira.fr","contact_number":"7869213370","city":null,"state":"Madhya Pradesh","country":"IN","group_id":175},{"id":"8","first_name":"Ajay","last_name":"Soni","email":"ajay.soni@aira.fr","contact_number":"9999999999","city":"Indore","state":"Madhya Pradesh","country":"IN","group_id":176}]

```

### Parameters

| Parameter | Description |
|------------|-------------|
|groupUid (string) | The ID of the group for which the group title is to be retrieved. |

### Return Value:

A string representing the group title.
Returns false if the specified group UID is not found.

### Usage:

Call the getGroupUsers function with the group UID to retrieve its group title. If the group UID exists, the function returns its group title; otherwise, it returns false.

## 9. cancelCase ():
The `cancelCase` function updates the case status from open to close for the specified case UID. If the case UID is not found, it returns `false`.

### Syntax:
```
const aira = require("AIRAFunction"); //Load Aira Function

async function cancelCase() {
 let airaObject = new aira(); //Create Aira Class Object

 let result = await airaObject.cancelCase('8','1224');
 console.log(JSON.stringify(result)); //Set Output in the current execution
}

cancelCase(); //function calling

//output
//{"message":"Case successfully cancel.."}

```

### Parameters

| Parameter | Description |
|------------|-------------|
|userId (string) |  The ID of the user initiating the cancellation. |
|caseUID (string)|  The UID of the case is to be cancelled. |

### Return Value:

A string indicating the updated status of the case (e.g., "Closed".)
Returns false if the specified case UID is not found.

### Usage:

Call the cancelCase function with the user ID and case UID to update the case status to "Closed". If the case UID exists and the status is successfully updated, the function returns the updated status; otherwise, it returns false.

## 10. openCase ():
The `openCase` function updates the case status from "Closed" to "Open" for the specified case UID. If the case UID is not found, it returns `false`.

### Syntax:
```
const aira = require("AIRAFunction"); //Load Aira Function

async function openCaseAction() {
 let airaObject = new aira(); //Create Aira Class Object

 let result = await airaObject.openCase('8','1224');
 console.log(JSON.stringify(result)); //Set Output in the current execution
}

openCaseAction(); //function calling

//output
//{"message":"Case successfully open.."}

openCase(userId, caseUID)
```

### Parameters

| Parameter | Description |
|------------|-------------|
|userId (string)|The ID of the user initiating the action.|
|caseUID (string)|The UID of the case to be opened.|

### Return Value:

A string indicating the updated status of the case (e.g., "Open").
Returns false if the specified case UID is not found.

### Usage:

Call the openCase function with the user ID and case UID to update the case status to "Open". If the case UID exists and the status is successfully updated, the function returns the updated status; otherwise, it returns false.
