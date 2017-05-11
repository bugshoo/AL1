**Create photos**
----
  <_Crea nuevas fotos especificando su Album_ID, id, title, url y thumbnail_>

* **URL**

  /photos

* **Method:**
  
  `POST`
  
*  **URL Params**

   None

* **Data Params**
   
   **Required:**
 
   `albumId=[integer]` <br />
   `id=[integer 255]` <br />
   `title=[string 255]` <br />
   `url=[string 255]` <br />
   `thumbnailUrl=[string 255]`
   
   **Example:**
  ```javascript 
    {
       "albumId"=[integer],
       "id"=[integer 255],
       "title"=[string 255],
       "url"=[string 255],
       "thumbnailUrl"=[string 255]
    }
  ```


* **Success Response:**

  _Returns a JSON object with the photo created_

  * **Code:** 201 OK<br />
    **Content:** 
    ```javascript
    {
        "albumId": 1,
        "id": 1,
        "title": "accusamus beatae ad facilis cum similique qui sunt",
        "url": "http://placehold.it/600/92c952",
        "thumbnailUrl": "http://placehold.it/150/92c952",
        "status": true
        }
    ```
 
* **Error Response:**

  * **Code:** 400 BAD REQUEST <br />
    **Content:** ```javascript { error : "The JSON is not valid" }```

  OR

  * **Code:** 422 UNPROCESSABLE ENTRY <br />
    **Content:** ```javascript{ error : "mandatory fields are missing", fields:[field1,field2,field3] }```

**Get a photo**
----
  _Get information about a single photo._

* **URL**

  _/photos/:id_

* **Method:**
  
  `GET`
  
* **URL Params**

   **Required:**
 
   `id=[integer]`

* **Data Params**

  _None._

* **Success Response:**
  
  _Returns a JSON object with the photo requested_

  * **Code:** 200 - OK <br />
    **Content:**
 ```javascript
 {
    "albumId": 1,
    "id": 1,
    "title": "accusamus beatae ad facilis cum similique qui sunt",
    "url": "http://placehold.it/600/92c952",
    "thumbnailUrl": "http://placehold.it/150/92c952",
    "status": true
    }
  ```
 
* **Error Response:**

  * **Code:** 404 NOT FOUND <br />
    **Content:** ```javascript{ error : "The photo not exists with the supplied id." }```
    
**Get photos**
----
  _Get information about several photos._

* **URL**

  _/photos_

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

  **albumId:** (asc | desc) <br />
  `?sort=albumId` for asc <br /> OR <br /> `?sort=-albumId` for desc
  
  **id:** (asc | desc) <br />
  `?sort=id` for asc <br /> OR <br /> `?sort=-id` for desc
  
  **title:** (asc | desc) <br />
  `?sort=title` for asc <br /> OR <br /> `?sort=-title` for desc
  
* **Query Params**

  **albumId:** (equal) <br />
  `?albumId__equal={value}`
  
  **id:** (equal) <br />
  `?id__equal={value}`
  
  **title:** (equal | like) <br />
  `?title__{operator}={value}`

* **Success Response:**
  
  _Returns a JSON object with the photos requested_

  * **Code:** 200 - OK <br />
    **Content:**
 ```javascript
 { "count"=[integer], 
   "value"=
           [
            {
              "albumId": 1,
              "id": 1,
              "title": "accusamus beatae ad facilis cum similique qui sunt",
              "url": "http://placehold.it/600/92c952",
              "thumbnailUrl": "http://placehold.it/150/92c952"
            },
            {
              "albumId": 1,
              "id": 2,
              "title": "reprehenderit est deserunt velit ipsam",
              "url": "http://placehold.it/600/771796",
              "thumbnailUrl": "http://placehold.it/150/771796"
            }
            ]
  }
  ```
 
* **Error Response:**

  * **Code:** 400 BAD REQUEST <br />
    **Content:** ```javascript{ error : "Query is not valid" }```
    
**Update photo**
----
  _Updates the information of a photo._

* **URL**

  _/photos/:id_

* **Method:**

  `PUT`
  
* **URL Params**

   **Required:**
 
   `id=[integer]`

* **Data Params**

   **Optional:**
 
   `albumId=[integer]` <br />
   `id=[integer 255]` <br />
   `title=[string 255]` <br />
   `url=[string 255]` <br />
   `thumbnailUrl=[string 255]`
   
   **Example:**

  ```javascript
  {
     "albumId"=[integer],
     "id"=[integer 255],
     "title"=[string 255],
     "url"=[string 255],
     "thumbnailUrl"=[string 255]
  }
  ```

* **Success Response:**

  _Returns a JSON object with the photo updated_

  * **Code:** 201 - OK <br />
    **Content:**
 ```javascript
 {
    "albumId": 1,
    "id": 1,
    "title": "accusamus beatae ad facilis cum similique qui sunt",
    "url": "http://placehold.it/600/92c952",
    "thumbnailUrl": "http://placehold.it/150/92c952"
  }
  ```
 
* **Error Response:**

  * **Code:** 400 BAD REQUEST <br />
    **Content:** ```javascript{ error : "The JSON is not valid" }```
    
  OR
    
  * **Code:** 404 NOT FOUND <br />
    **Content:** ```javascript{ error : "Photo not exists with the supplied id." }```
    
**Delete a photo**
----
  _Deletes a photo._

* **URL**

  _/photos/:id_

* **Method:**
  
  `DELETE`
  
* **URL Params**

  **Required:**
 
  `id=[integer]`

* **Data Params**

  _None._

* **Success Response:**

  * **Code:** 204 - OK <br />
    **Content:** ```{ error : "Photo deleted successfully" }```
 
* **Error Response:**

  * **Code:** 404 NOT FOUND <br />
    **Content:** ```{ error : "Photo not exists the supplied id." }```
