**Title**
----
  <_Additional information about your API call. Try to use verbs that match both request type (fetching vs modifying) and plurality (one vs multiple)._>

* **URL**

  <_The URL Structure (path only, no root url)_>

* **Method:**
  
  <_The request type_>

  `GET` | `POST` | `DELETE` | `PUT`
  
*  **URL Params**

   <_If URL params exist, specify them in accordance with name mentioned in URL section. Separate into optional and required. Document data constraints._> 

   **Required:**
 
   `id=[integer]`

   **Optional:**
 
   `photo_id=[alphanumeric]`

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