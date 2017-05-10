**Create ToDo task**
----
  _Creates a single ToDo task._

* **URL**

  _/todos_

* **Method:**

  `POST`
  
* **URL Params**

  _None._

* **Data Params**

   **Required:**
 
   `userId=[integer]` <br />
   `title=[string 255]` <br />
   `completed=[boolean]`
   
   **Example:**

  `{
     "userId": [integer],
     "title": [string 255],
     "completed": [boolean]
  }`

* **Success Response:**

  _Returns a JSON object with the task created_

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

  _/todos/:id_

* **Method:**
  
  `GET`
  
* **URL Params**

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
  
* **URL Params**

  _None._

* **Data Params**

  _None._
  
* **Paging Params**

  **offset:** 0 by default <br />
  `?offset=[integer]`
  
  **limit:** 5 by default <br />
  `?limit=[integer]`
  
* **Sorting Params**

  **title:** (asc | desc) <br />
  `?sort=title` for asc <br /> OR <br /> `?sort=-title` for desc
  
* **Query Params**

  **userId:** (equal) <br />
  `?userId__equal={value}`
  
  **title:** (equal | like) <br />
  `?title__{operator}={value}`
  
  **completed:** (equal) <br />
  `?completed__equal={value}`

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
    
**Update ToDo task**
----
  _Updates the information of a ToDo task._

* **URL**

  _/todos/:id_

* **Method:**

  `PUT`
  
* **URL Params**

   **Required:**
 
   `id=[integer]`

* **Data Params**

   **Optional:**
 
   `userId=[integer]` <br />
   `title=[string 255]` <br />
   `completed=[boolean]` <br />
   
   **Example:**

  `{
     "userId": [integer],
     "title": [string],
     "completed": [boolean]
   }`

* **Success Response:**

  _Returns a JSON object with the task updated_

  * **Code:** 200 - OK <br />
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
    
  * **Code:** 404 NOT FOUND <br />
    **Content:** `{ error : "No task exists with the supplied ID." }`
    
**Delete a ToDo task**
----
  _Deletes a ToDo task._

* **URL**

  _/todos/:id_

* **Method:**
  
  `DELETE`
  
* **URL Params**

  **Required:**
 
  `id=[integer]`

* **Data Params**

  _None._

* **Success Response:**

  * **Code:** 204 - OK <br />
    **Content:**
    _empty_
 
* **Error Response:**

  * **Code:** 404 NOT FOUND <br />
    **Content:** `{ error : "No task exists with the supplied ID." }`
