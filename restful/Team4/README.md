
LIST ALBUMS

Returns json data about a set of albums

	URL	
		/albums
		
	Method
		GET 

	URL Params

		Requiered:
		offset=[integer, start in 0]
		limit=[integer, 10]

		Optional:
		name_order = [asc | des]
		userID_filter = [=]
		title_filter = [ = | %pattern%]

		

	Data Params
		none

	Sucess Response:
		Code:200
		Content: [
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
		Required:

		id=[integer, unique]
		username=[string, unique, maximum = 55]
		email=[string, format_validation = example@example.com, maximum = 255]
		
		Optional:

		name=[string, maximum = 255]
		address=[
					street=[string, maximum = 255]
					suite=[string, maximum = 55]
					city=[string, maximum = 55]
					zipcode=[string, maximum = 32]
					geo=[
						lat=[double, signed]
						lng=[double, signed]
					]
				]
				phone=[string, maximum = 55]
				website=[string, maximum = 255]
				company=[
					name=[string, maximum = 255]
					catchPhrase=[string, maximum = 255]
					bs=[string, maximum = 255]
				]

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

		