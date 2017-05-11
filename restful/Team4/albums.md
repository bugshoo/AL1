
**LIST ALBUMS**
----

Returns json data about a set of ten albums by page


	* **URL:**	
		_/albums_

	* **Method:**
		`GET`

	* **URL Params:**

		**Requiered:**
		offset = start in 0  default [integer]
		limit = 10 default [integer]

		**Optional:**

			**Order:**
			name_order = "asc" default [string, value: asc | des]
		
			**Filter:**
			userID_filter = 11 [integer, operator: equal ]
			title_filter = "Vacations" [string, operator: equal | like]

		

	* **Data Params:**
		none

	* **Sucess Response:**
		* **Code:**200
		**Content:** [
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

	* **Error Response:**
		* **Code:**401 BAD REQUEST 
		**Content:**{error:  the request was invalid or cannot be served, the parameters are invalid.}

	* **Sample Call:**
		$.ajax({
		    url: "/albums",
		    dataType: "json",
		    type : "GET",
		    success : function(r) {
		     	console.log(r);
		    }
	  	});


		