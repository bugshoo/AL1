
<h1 align="center">API ALBUMS</h1>

<br>


  |    SERVICE   |    METHOD    |       URL      |  DESCRIPTION |
  |--------------|--------------|:--------------:|-------------:|
  |List albums   |GET           |_/albums_       |              |
  |Create albums |              |                |              |
  |Delete albums |              |                |              |
  |Update albmums|              |                |              |


**LIST ALBUMS**
----

Returns json data about a set of ten albums by page

  * **URL:**	

    _/albums_
  
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

