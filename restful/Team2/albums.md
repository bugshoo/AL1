**Create album**
----
_Create a new album._

* **URL**
_/albums_
 
* **Method:**
  
  `POST` 
  
*  **URL Params**

  **Required:**
 
None

* **Data Params**

 {
    "userId": `[integer]`,
     "title": ´[string]`,
  } 

* **Success Response:**
  
   * **Code:** 201 OK <br />
    **Content:** ` {  "userId": 1,    "id": 1,    "title": "quidem molestiae enim"  },`
 
* **Error Response:**

  * **Code:** 400  BAD REQUEST- <br />
    **Content:** `{error: "The JSON is not valid"}`

  OR

  * **Code:** 422 UNPROCESSABLE ENTRY <br />
    **Content:** `{ error : "mandatory fields are missing" }`

