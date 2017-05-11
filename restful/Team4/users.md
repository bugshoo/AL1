**CREATE USER**

Create a single user

	*URL	
		rest/v1/users

	*Method
		POST

	*URL Params

		None

		Optional:
			None

	*Data Params
		
        Required:

		name=[string, maximum = 255]
		username=[string, unique, maximum = 55]
		email=[string, format_validation = example@example.com, maximum = 255]
		
		Optional:

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

	*Sucess Response:
		Code:201
		Content: [
			 {
			    "user": {
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
                },
				"msg": "User created correctly"
		  	 }
		]

	*Error Response:
		
		Code:401 BAD REQUEST 
		Content:{error:  the request was invalid, {field1, field2,...,fieldn} don't have the specified format.}

		Code:422 UNPROCESSABLE ENTITY
		Content:{error: {field1, field2,.., fieldn} are missing in the payload}

	*Sample Call:
		$.ajax({
		    url: "/users",
		    dataType: "json",
		    type : "POST",
			data : "{
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

	*Notes:
        id:[assigned by the service]

**LIST USERS**

List all users by filters and an order

    *URL	
		rest/v1/users

	*Method
		GET

	*URL Params

        Requiered:
	        offset=[integer] 
	        limit=[integer, default=20]
            example: rest/v1/users?offset=0&limit=8

	    Optional:
            name_order = [asc | des] 
            order by name asc example : rest/v1/users?offset=0&limit=8&name_order=asc  
            userID_filter = [=]
            filter by userID, equal to, example : rest/v1/users?offset=0&limit=8&userID_filter=2 
            title_filter = [ = | %pattern%]
            filter by title, equal to, example : rest/v1/users?offset=0&limit=8&title_filter=Manu 
            filter by title, like, example : rest/v1/users?offset=0&limit=8&title_filter=%M% //title that start with M
            
    *Data Params
        none

    *Sucess Response:
        Code:200
        Content:  [
                    totalCounts:2,
                    list_users:{
                            {
                                "id": 1,
                                "name": "Leanne Graham",
                                "username": "Bret",
                                "email": "Sincere@april.biz",
                                "address": {
                                "street": "Kulas Light",
                                "suite": "Apt. 556",
                                "city": "Gwenborough",
                                "zipcode": "92998-3874",
                                "geo": {
                                    "lat": "-37.3159",
                                    "lng": "81.1496"
                                }
                                },
                                "phone": "1-770-736-8031 x56442",
                                "website": "hildegard.org",
                                "company": {
                                "name": "Romaguera-Crona",
                                "catchPhrase": "Multi-layered client-server neural-net",
                                "bs": "harness real-time e-markets"
                                }
                            },
                            {
                                "id": 2,
                                "name": "Ervin Howell",
                                "username": "Antonette",
                                "email": "Shanna@melissa.tv",
                                "address": {
                                "street": "Victor Plains",Notes
                                "suite": "Suite 879",
                                "city": "Wisokyburgh",
                                "zipcode": "90566-7771",
                                "geo": {
                                    "lat": "-43.9509",
                                    "lng": "-34.4618"
                                }
                                },
                                "phone": "010-692-6593 x09125",
                                "website": "anastasia.net",
                                "company": {
                                "name": "Deckow-Crist",
                                "catchPhrase": "Proactive didactic contingency",
                                "bs": "synergize scalable supply-chains"
                                }
                            }
                    }
	             ]
        *Error Response:
           	Code:401 BAD REQUEST 
		    Content:{error:  the request was invalid, {field1, field2,...,fieldn} don't have the specified format.}

        *Sample Call:
            $.ajax({
                url: "/albums",
                dataType: "json",
                type : "GET",
                success : function(r) {
                    console.log(r);
                }
            });

        *Notes: