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
{
  {
      "albumId": [integer],
      "id": [integer],
      "title": [string],
      "url": [string],
      "thumbnailUrl": [string]
  }
} 

* **Success Response:**

  * **Code:** 201 OK<br />
    **Content:** 
    `{
        {
          "albumId": [integer],
          "id": [integer],
          "title": [string],
          "url": [string],
          "thumbnailUrl": [string],
          "status": [true]
        }
      }`
 
* **Error Response:**

  * **Code:** 400 BAD REQUEST <br />
    **Content:** `{ error : "The JSON is not valid" }`

  OR

  * **Code:** 422 UNPROCESSABLE ENTRY <br />
    **Content:** `{ error : "mandatory fields are missing" }`

