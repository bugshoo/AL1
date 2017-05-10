
LIST ALBUMS

Returns json data about a set of albums

	URL	
		/albums

	Method
		GET 

	URL Params

		Requiered:
		none

		Optional:
		offset=[integer]
		limit=[integer]

	Data Params
		none

	Sucess Response:
		Code:200
		Content: [
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
		]

	Error Response:
		Code:401 BAD REQUEST 
		Content:{error:  the request wos invalid or cannot be served.}

	Sample Call:
		$.ajax({
		    url: "/albums",
		    dataType: "json",
		    type : "GET",
		    success : function(r) {
		     	console.log(r);
		    }
	  	});

	Notes:


// USERS API CRUD
CREATE USER

Create a single user

	URL	
		/users

	Method
		POST

	URL Params

		None

		Optional:
			None

	Data Params
		Requiered:
		id=[integer]
		name=[string]
		username=[string]
		email=[string]
		address=[
			street=[string]
			suite=[string]
			city=[string]
			zipcode=[string]
			geo=[
				lat=[double]
				lng=[double]
			]
		]
		phone=[string]
		website=[string]
		company=[
			name=[string]
			catchPhrase=[string]
			bs=[string]
		]
		
		Optional:
		None

	Sucess Response:
		Code:200
		Content: [
			 {
			    "userId": 1,
				"msg": "User created correctly"
		  	 }
		]

	Error Response:
		
		Code:401 BAD REQUEST 
		Content:{error:  the request wos invalid or cannot be served.}

		Code:422 UNPROCESSABLE ENTITY
		Content:{error: fields are missing in the payload}

	Sample Call:
		$.ajax({
		    url: "/users",
		    dataType: "json",
		    type : "POST",
			data : "{
    			"id": 2,
				"name": "Ervin Howell",
				"username": "Antonette",
				"email": "Shanna@melissa.tv",
				"address": {
				"street": "Victor Plains",
				"suite": "Suite 879",
				"city": "Wisokyburgh",
				"zipcode": "90566-7771",
				"geo": {
					"lat": "-43.9509",
					"lng": "-34.4618"
				}
    		}",
		    success : function(r) {
		     	console.log(r);
		    }
	  	});

	Notes:

		