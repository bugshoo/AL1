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
```javascript
 {
    "userId": `[integer]`,
    "title": `[string]`,
  } `
```
* **Success Response:**
  
   * **Code:** 201 OK <br />
    **Content:** ` {  "userId": 1,    "id": 1,    "title": "quidem molestiae enim"  }`
 
* **Error Response:**

  * **Code:** 400  BAD REQUEST- <br />
    **Content:** `{error: "The JSON is not valid"}`

  OR

  * **Code:** 422 UNPROCESSABLE ENTRY <br />
    **Content:** `{ error : "mandatory fields are missing,fields:[field1,field2]" }`

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
* **Paging Params**

  **offset:** 0 by default <br />
  `?offset=[integer]`
  
  **limit:** 10 by default <br />
  `?limit=[integer]`
  
* **Sorting Params**

  **title:** (asc | desc) <br />
  `?sort=title` for asc <br /> OR <br /> `?sort=-title` for desc
  
* **Query Params**

  **userId:** (equal) <br />
  `?userId__equal={value}`
  
  **title:** (equal | like) <br />
  `?title__{operator}={value}`
  
  
  * **Success Response:**

  * **Code:** 200 OK <br />
    **Content:** ```javascript[
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
  }]```
 
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

  * **Code:** 400 BAD REQUEST <br />
    **Content:** `{ error : "Query is not valid" }`

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
  
  **Optional:**
 
   `userId=[integer]` <br />
   `title=[string 255]` <br />
   `completed=[boolean]` <br />
   
   **Example:**
```javascript
  {
     "userId": [integer],
     "title": [string],
     }
```     
* **Success Response:**

  * **Code:** 201 OK <br />
    **Content:** `{  "userId": 1,    "id": 1,    "title": "quidem molestiae enim-2"  }`
 
* **Error Response:**

  * **Code:** 404 NOT FOUND <br />
    **Content:** `{ error : "This album doesn't exist" }`
    
    OR
    
   * **Code:** 422 UNPROCESSABLE ENTRY <br />
    **Content:** `{ error : "mandatory fields are missing",,fields:[field1,field2] }`
    
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

  * **Code:** 203 – OK  <br />
    **Content:** `{The resource was successfully deleted }`
 
* **Error Response:** 

  * **Code:** 404 NOT FOUND <br />
    **Content:** `{ error : "This album doesn't exist" }` 
