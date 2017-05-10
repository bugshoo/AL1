**Create ToDo task**
----
  _Creates a single ToDo task ._

* **URL**

  _/todos_

* **Method:**

  `POST`
  
*  **URL Params**

   _None_ 

* **Data Params**

  `{
     "userId": [integer],
     "title": [string],
     "completed": [boolean]
  }`

* **Success Response:**

  * **Code:** 201 - OK <br />
    **Content:**
 `{
    "userId": 1,
    "id": 4, 
    "title": "et porro tempora",
    "completed": true
    }`
 
* **Error Response:**

  * **Code:** 400 BAD REQUEST <br />
    **Content:** `{ error : "The JSON is not valid" }`

  OR

  * **Code:** 422 UNPROCESSABLE ENTITY <br />
    **Content:** `{ error : "Mandatory fields are missing" }`
    
**Get a ToDo task**
----
  _Get information about a single task._

* **URL**

  <_/todos/:id_>

* **Method:**
  
  `GET`
  
*  **URL Params**

   **Required:**
 
   `id=[integer]`

* **Data Params**

  _None._

* **Success Response:**
  
  _Returns a JSON object with the task requested_

  * **Code:** 200 - OK <br />
    **Content:**
 `{
    "userId": 1,
    "id": 4, 
    "title": "et porro tempora",
    "completed": true
    }`
 
* **Error Response:**

  * **Code:** 404 NOT FOUND <br />
    **Content:** `{ error : "No task exists with the supplied ID." }`
    
**Get ToDo tasks**
----
  _Get information about several tasks._

* **URL**

  _/todos_

* **Method:**
  
  `GET`
  
*  **URL Params**

   _None._

* **Data Params**

  _None._

* **Success Response:**
  
  _Returns a JSON object with the tasks requested_

  * **Code:** 200 - OK <br />
    **Content:**
 `[
  {
    "userId": 1,
    "id": 1,
    "title": "delectus aut autem",
    "completed": false
  },
  {
    "userId": 1,
    "id": 2,
    "title": "quis ut nam facilis et officia qui",
    "completed": false
  }
  ]`
 
* **Error Response:**

  * **Code:** 404 NOT FOUND <br />
    **Content:** `{ error : "No task found in the database." }`
