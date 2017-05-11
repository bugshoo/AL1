<h1 align="center">API Photos</h1>
<p align="center">Created by: Team4 Contact: dreamteam@alertLogic.com</p>

----
<br />

  |    SERVICE   |    METHOD    |           URL          |                 DESCRIPTION                    |
  |--------------|--------------|:----------------------:|-----------------------------------------------:|
  |List photos   |GET           |_/rest/v1/photos_       |                                                |
  |Create photos |POTS          |_/rest/v1/photos_       |                                                |
  |Delete photos |Delete        |_/rest/v1/photos_       |                                                |
  |Update photos |PUT           |_/rest/v1/photos_       |                                                |


<br />
**LIST PHOTOS**
----

Returns json data about a set of ten photos by page

  * **URL:**  

    _/rest/v1/photos_
  
  * **METHOD:**

    `GET`
  
* **URL PARAMS:**

    * **Requiered:**
    
      offset = start in 0  default `[integer]`<br />
      limit = 10 default `[integer]`

      * **Example** *
        example: rest/v1/photos?offset=0&limit=8


    * **Optional:**
    
      * **Order:**
      
        name_order = "asc" `default` `[string, value: asc | des]`

        * **Examples** *
          by order ascendent  = rest/v1/photos?offset=0&limit=8&name_order=asc
          by order descendent = rest/v1/photos?offset=0&limit=8&name_order=des 
        
      * **Filter:**
        
        albumId_filter = 11 `[integer, operator: equal] `<br />
        title_filter = "Vacations" `[string, operator: equal | like]`

        * ** Examples** *
          by albumId equal to 2 = rest/v1/photos?offset=0&limit=8&albymId_filter=2
          by title equal to flower = rest/v1/photos?offset=0&limit=8&title_filter=flower 

    

* **DATA PARAMS:**

  none

* **SUCESS RESPONSE:**

  * **Code:** 200 <br />
  **Content:**<br />
  ```
  [
    totalCounts:100,
    list_photos:{
      {
        "albumId": 1,
        "id": 1,
        "title": "accusamus beatae ad facilis cum similique qui sunt",
        "url": "http://placehold.it/600/92c952",
        "thumbnailUrl": "http://placehold.it/150/92c952"
      },
        
      .
      .
      .
          
      {
        "userId": n,
        "id": n,
        "title": "title n",
        "url": "http://placehold.it/600/photoN",
        "thumbnailUrl": "http://placehold.it/600/photoN"
      } 
    }
  ]
  ```

* **ERROR RESPONSE:**

  * **Code:** 401 BAD REQUEST <br />
  **Content:**<br />
  `{error:  the request was invalid or cannot be served, the parameters are invalid.}`

  * **Sample Call:**
  ```javascrip
    $.ajax({
        url: "/photo",
        dataType: "json",
        type : "GET",
        success : function(r) {
          console.log(r);
        }
      });
   ```

**CREATE PHOTOS**
----
This service create a photo

* **URL**<br />
  _/photos_
 
* **METHOD:**
  
  `POST` 
  
*  **URL PARAMS:**

o  * **Required:**
 
    None

* **DATA PARAMS:**
  ```javascript
  {
        "albumId": `[integer]`,
        "title": `[string]`,
        "url": `[string]`,
        "thumbnailUrl": `[string]`,
    } 
   ```

* **SUCESS RESPONSE:**
  
   * **Code:** 201 OK <br />
    **Content:** <br />
    ```
    {
      "albumId": n,
      "id": n,
      "title": "title n",
      "url": "http://placehold.it/600/photoN",
      "thumbnailUrl": "http://placehold.it/150/photoN" 
  }
  ```
 
* **ERROR RESPONSE:**

  * **Code:** 400  BAD REQUEST- <br />
    **Content:** <br />
    `{error: "The JSON is not valid"}`


  * **Code:** 422 UNPROCESSABLE ENTRY <br />
    **Content:** <br />
    `{ error : "Mandatory fields are missing" }`


**EDIT PHOTO**
----
  Returns json data about a photo update.

* **URL**

  /photo/:id

* **Method:**

  `PUT`
  
*  **URL Params**
  
  **Required:**
 
   `id=[integer]`  
  

* **Data Params**