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
    **Content:** ` {  "userId": 1,    "id": 1,    "title": "quidem molestiae enim"  }`
 
* **Error Response:**

  * **Code:** 400  BAD REQUEST- <br />
    **Content:** `{error: "The JSON is not valid"}`

  OR

  * **Code:** 422 UNPROCESSABLE ENTRY <br />
    **Content:** `{ error : "mandatory fields are missing" }`

**List Albums**
----
  Returns json data about all the albums.

* **URL**

  _/albums/_

* **Method:**

  `GET`
  
* **URL Params**
 
 **Required:**
  
  None 
  
* **Data Params**

  None

* **Success Response:**

  * **Code:** 200 OK <br />
    **Content:** `[
  {
    "userId": 1,
    "id": 1,
    "title": "quidem molestiae enim"
  },
  {
    "userId": 1,
    "id": 2,
    "title": "sunt qui excepturi placeat culpa"
  },
  {
    "userId": 1,
    "id": 3,
    "title": "omnis laborum odio"
  },
  {
    "userId": 1,
    "id": 4,
    "title": "non esse culpa molestiae omnis sed optio"
  }]`
 
* **Error Response:**

  * **Code:** 404 NOT FOUND <br />
    **Content:** `{ error : "This albums don't exist" }`

**Show Albums**
----
  Returns json data about a single album.

* **URL**

  /albums/:id

* **Method:**

  `GET`
  
*  **URL Params**

   **Required:**
 
   `id=[integer]`

* **Data Params**

  None

* **Success Response:**

  * **Code:** 200 OK <br />
    **Content:** `{
    "userId": 1,
    "id": 1,
    "title": "quidem molestiae enim"
  }`
 
* **Error Response:**

  * **Code:** 404 NOT FOUND <br />
    **Content:** `{ error : "This album doesn't exist" }`

**Edit Album**
----
  Returns json data about a album update.

* **URL**

  /albums/:id

* **Method:**

  `PUT`
  
*  **URL Params**
  
  **Required:**
 
   `id=[integer]`  
  

* **Data Params**
 {
    "userId": `[integer]`,
     "title": ´[string]`,
  } 
     
* **Success Response:**

  * **Code:** 200 OK <br />
    **Content:** `{  "userId": 1,    "id": 1,    "title": "quidem molestiae enim-2"  }`
 
* **Error Response:**

  * **Code:** 404 NOT FOUND <br />
    **Content:** `{ error : "This album doesn't exist" }`
    
    OR
    
   * **Code:** 422 UNPROCESSABLE ENTRY <br />
    **Content:** `{ error : "mandatory fields are missing" }`
    
**Delete Album**
----
  Returns json data about a deleted photo.

* **URL**

  /albums/:id

* **Method:**

  `DELETE`
  
*  **URL Params**
  
  id=[integer]

* **Data Params**

  None
  
* **Success Response:**

  * **Code:** 203 – OK – The resource was successfully deleted <br />
    **Content:** ``
 
* **Error Response:**

  * **Code:** 404 NOT FOUND <br />
    **Content:** `{ error : "This album doesn't exist" }` 
