# Trigger Function


## Triggers In AIRA Workflow

Triggers within the AIRA workflow serve as a mechanism to apply specific business logic based on predefined conditions or events. They play a crucial role in enhancing workflow customization and automation, ensuring that precise actions are executed according to specific requirements.

## Trigger Functions in AIRA

AIRA has developed trigger functions to simplify the process of creating triggers, making it more convenient for users to implement their desired logic within workflows. These trigger functions provide pre-defined functionalities that can be easily incorporated into triggers, streamlining the trigger creation process and enhancing overall workflow efficiency.

## 1. executeQuery()

The executeQuery function retrieves data from a MySQL database by executing a specified SQL query using the provided MySQL connection ID.

### Syntax:

```
const aira = require("AIRAFunction"); 

async executeQuery(query, conn_id) {
    const { dbKenx, message } = await this.getConnection(conn_id);
    if (message.status === true) {
      try {
        const queryResult = await dbKenx.raw(query);
        const stringifyResult = JSON.stringify(queryResult[0]);
        const queryParseResult = JSON.parse(stringifyResult);
        return queryParseResult;
        
      } catch (error) {
        console.error("Error executing query:", error);
        return false;
      } finally {
        dbKenx.destroy();
      }
    } else {
      console.error("Error connecting to the database:", message.error);
      return false;
    }
  }

executeQuery(query, conn_id)
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
const aira = require("AIRAFunction"); 

async getCurrentDate() {
    const currentDate = new Date();
    const year = currentDate.getFullYear();
    const month = String(currentDate.getMonth() + 1).padStart(2, "0"); // Month is zero-based, so we add 1
    const date = String(currentDate.getDate()).padStart(2, "0");
    return `${year}-${month}-${date}`;
  }

getCurrentDate()
```

### Usage:
Call the getCurrentDate function when you need to retrieve the current date in your program or workflow.

## 3. getCurrentTime()

The getCurrentTime function returns the current time.

### Syntax:

```
const aira = require("AIRAFunction"); 

async getCurrentTime() {
    const currentTime = new Date();
    const hours = String(currentTime.getHours()).padStart(2, "0");
    const minutes = String(currentTime.getMinutes()).padStart(2, "0");
    const seconds = String(currentTime.getSeconds()).padStart(2, "0");
    return `${hours}:${minutes}:${seconds}`;

getCurrentTime()
```


### Usage:
Call the getCurrentTime function when you need to retrieve the current time in your program or workflow.


## 4. userInfo()

The userInfo function retrieves information about a user with a given ID.

### Syntax:

```
const aira = require("AIRAFunction");

async userInfo(user_id) {
    const db = knex(this.connection); // Use this.connection here
    try {
      const userResult = await db.raw(
        `select first_name,last_name,email,country_code,contact_number,status,created_at,updated_at,position,address,city, CASE
        WHEN status = 1 THEN 'Active'
        WHEN status = 0 THEN 'Inactive'
        ELSE 'Unknown'
      END AS status,country,zipcode from users where id = '${user_id}'`
      );
      const stringifyUser = JSON.stringify(userResult[0]);
      const userParseResult = JSON.parse(stringifyUser);
      return userParseResult;
    } catch (error) {
      return error;
    } finally {
      db.destroy();
    }
  }

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
const aira = require("AIRAFunction");

async groupList(regex = null, start = null, limit = null) {
    const db = knex(this.connection); // Use this.connection here
    try {
      const groupResult = await db.raw(
        `SELECT id,
        name,
        CASE
          WHEN status = 1 THEN 'Active'
          WHEN status = 0 THEN 'Inactive'
          ELSE 'Unknown'
        END AS status,
        description
      FROM groups
      WHERE name LIKE '%${regex}%'
      LIMIT ${start}, ${limit};`
      );
      const stringifyGroup = JSON.stringify(groupResult[0]);
      const groupParseResult = JSON.parse(stringifyGroup);
      return groupParseResult;
    } catch (error) {
      return error;
    } finally {
      db.destroy();
    }
  }

groupList(regex = null, start = null, limit = null)
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
const aira = require("AIRAFunction");

async getGroupUID(groupName) {
    const db = knex(this.connection); // Use this.connection here
    try {
      const groupResult = await db.raw(
        `SELECT id as groupId FROM groups WHERE name = '${groupName}'`
      );
      const stringifyGroup = JSON.stringify(groupResult[0]);
      const groupParseResult = JSON.parse(stringifyGroup);
      if (Object.keys(groupParseResult).length === 0) {
        return false;
      }
      return groupParseResult;
    } catch (error) {
      return error;
    } finally {
      db.destroy();
    }
  }

getGroupUID(groupName)
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
const aira = require("AIRAFunction");

async getGroupName(groupUid) {
    const db = knex(this.connection); // Use this.connection here
    try {
      const groupResult = await db.raw(
        `SELECT name FROM groups WHERE id = '${groupUid}'`
      );
      const stringifyGroup = JSON.stringify(groupResult[0]);
      const groupParseResult = JSON.parse(stringifyGroup);
      if (Object.keys(groupParseResult).length === 0) {
        return false;
      }
      return groupParseResult;
    } catch (error) {
      return error;
    } finally {
      db.destroy();
    }
  }

getGroupName(groupUid)
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

const aira = require("AIRAFunction");

async getGroupUsers(groupUid) {
      const db = knex(this.connection); // Use this.connection here
      try {
        const groupResult = await db.raw(
          `SELECT users.id, users.first_name,users.last_name,users.email,users.contact_number,users.city, users.state,users.country,group_user.id as group_id FROM group_user LEFT JOIN users ON users.id = group_user.user_id WHERE group_id = '${groupUid}'`
        );
        const stringifyGroup = JSON.stringify(groupResult[0]);
        const groupParseResult = JSON.parse(stringifyGroup);
        if (Object.keys(groupParseResult).length === 0) {
          return false;
        }
        return groupParseResult;
      } catch (error) {
        return error;
      } finally {
        db.destroy();
      }
    }

getGroupUsers(groupUid)
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
const aira = require("AIRAFunction");

async cancelCase(userId, caseUID) {
    const db = knex(this.connection); // Use this.connection here
    try {
      const fields = await db.raw(
        "UPDATE job_activity_delegation SET status = 'CLOSED' WHERE id = " +
          caseUID +
          " and `current_user` = " +
          userId
      );
      const queryConnectionResult = JSON.stringify(fields[0]);
      var json = JSON.parse(queryConnectionResult);
      let result = { message: "Case successfully canceld.." };
      return result;
    } catch (error) {
      return error.sqlMessage + "--" + error.sql;
    } finally {
      db.destroy();
    }
  }

cancelCase(userId, caseUID)
```

### Parameters

| Parameter | Description |
|------------|-------------|
|userId (string) |  The ID of the user initiating the cancellation. |
|caseUID (string)|  The UID of the case is to be canceled. |

### Return Value:

A string indicating the updated status of the case (e.g., "Closed".)
Returns false if the specified case UID is not found.

### Usage:

Call the cancelCase function with the user ID and case UID to update the case status to "Closed". If the case UID exists and the status is successfully updated, the function returns the updated status; otherwise, it returns false.



## 10. openCase ():
The `openCase` function updates the case status from "Closed" to "Open" for the specified case UID. If the case UID is not found, it returns `false`.

### Syntax:
```
const aira = require("AIRAFunction");

async openCase(userId, caseUID) {
    const db = knex(this.connection); // Use this.connection here
    try {
      const fields = await db.raw(
        "UPDATE job_activity_delegation SET status = 'OPEN' WHERE id = " +
          caseUID +
          " and `current_user` = " +
          userId
      );
      const queryConnectionResult = JSON.stringify(fields[0]);
      var json = JSON.parse(queryConnectionResult);
      let result = { message: "Case successfully open.." };
      return result;
    } catch (error) {
      return error.sqlMessage + "--" + error.sql;
    } finally {
      db.destroy();
    }
  }

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



## 11. getAccessToken ():
The `getAccessToken` function retrieves an access token using the provided email and password credentials.

### Syntax:
```
const aira = require("AIRAFunction");

async getAccessToken(email, password) {
    let data = JSON.stringify({
      email: email,
      password: password,
    });
    const httpsAgent = new https.Agent({
      rejectUnauthorized: false,
    });
    let accessToken = "";
    let config = {
      method: "post",
      maxBodyLength: Infinity,
      httpsAgent: httpsAgent,
      url: "https://trial.aira.technology/api/v1/auth/login",
      headers: {
        "Content-Type": "application/json",
      },
      data: data,
    };
    await axios
    .request(config)
    .then((response) => {
      accessToken = {
        token: response.data.token,
      };
    })
    .catch((error) => {
      accessToken = {
        error: error,
      };
    });
    return accessToken;
  }

getAccessToken(email, password)
```
### Parameters

| Parameter | Description |
|------------|-------------|
|email (string)| The email address associated with the user account.|
|password (string)| The password for the user account.|

### Return Value:

A string representing the access token. It
returns null or an empty string if the access token cannot be obtained using the provided credentials.

### Usage:

Call the getAccessToken function with the user's email and password to retrieve an access token. If the email and password are valid and the access token is successfully obtained, the function returns the access token; otherwise, it returns null or an empty string.

