
<h1 align="center">API ALBUMS</h1>
<p align="center">Created by: Team4 Contact: dreamteam@alertLogic.com</p>

----
<br />

  |    SERVICE   |    METHOD    |           URL          |  		   DESCRIPTION	                  |
  |--------------|--------------|:----------------------:|-----------------------------------------------:|
  |List albums   |GET           |_/rest/v1/albums_       |              			          |
  |Create albums |POTS          |_/rest/v1/albums_     	 |              				  |
  |Delete albums |              |                	 |                				  |
  |Update albmums|              |                	 |                                                |


<br />
**LIST ALBUMS**
----

Returns json data about a set of ten albums by page

  * **URL:**	

    _/rest/v1/albums_
  
  * **METHOD:**

    `GET`
  
* **URL PARAMS:**

    * **Requiered:**
    
      offset = start in 0  default `[integer]`<br />
      limit = 10 default `[integer]`


    * **Optional:**
    
      * **Order:**
      
        name_order = "asc" `default` `[string, value: asc | des]`
        
      * **Filter:**
        
        userID_filter = 11 `[integer, operator: equal] `<br />
        title_filter = "Vacations" `[string, operator: equal | like]`

		

* **DATA PARAMS:**

  none

* **SUCESS RESPONSE:**

  * **Code:** 200 <br />
  **Content:**<br />
  ```
  [
	  totalCounts:100,
		list_albums:{
			{
				"userId": 1,
				"id": 1,
				"title": "quidem molestiae enim"
			},
				
			.
			.
			.
			  	
			{
			  	"userId": n,
				"id": n,
				"title": "title n"
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
		    url: "/albums",
		    dataType: "json",
		    type : "GET",
		    success : function(r) {
		     	console.log(r);
		    }
	  	});
   ```

**CREATE ALBUM**
----
This service create an album of pictures

* **URL**<br />
	_/albums_
 
* **METHOD:**
  
  `POST` 
  
*  **URL PARAMS:**

	* **Required:**
 
		None

* **DATA PARAMS:**
	```javascript
 	{
    		"userId": `[integer]`,
    		"title": `[string]`,
  	} 
 	 ```

* **SUCESS RESPONSE:**
  
   * **Code:** 201 OK <br />
    **Content:** <br />
    ```
    {
    	"userId": n,
		"id": n,
		"title": "title n"
	}
	```
 
* **ERROR RESPONSE:**

  * **Code:** 400  BAD REQUEST- <br />
    **Content:** <br />
    `{error: "The JSON is not valid"}`


  * **Code:** 422 UNPROCESSABLE ENTRY <br />
    **Content:** <br />
    `{ error : "Mandatory fields are missing" }`


**EDIT ALBUM**
----
  Returns json data about a album update.

* **URL**

  /albums/:id

* **METHOD:**

  `PUT`
  
*  **URL PARAMS**
	* **Required:**
		`id=[integer]`  
  	* **Optional:**

* **DATA PARAMS:**
{
"userId": `[integer]`,
"title": `[string]`,
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
    
