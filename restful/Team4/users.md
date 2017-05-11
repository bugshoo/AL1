

<h1 align="center">API USERS</h1>

<br>


  |    SERVICE   |    METHOD    |       URL      |  DESCRIPTION |
  |--------------|--------------|:--------------:|-------------:|
  |List users    |GET           |_/rest/v1/users/_       | List all users by filters and an order|
  |Create users  |POST          |_/rest/v1/users_        | Create a single user             |
  |Delete users  |DELETE              |_/rest/v1/users/:IDuser_                 | Delete a single user  |
  |Update users  |PUT           |   _/rest/v1/users/:IDuser_|  Update a single user            |

</br>


**CREATE USER**

Create a single user

* **URL**
	_/rest/v1/users_

* **Method**
	
	`POST`

* **URL Params** 

		None

		Optional:
			None

* **Data Params** 
		
		Required:

			name = `[string, maximum = 255]`
			username = `[string, unique, maximum = 55]`
			email = `[string, format_validation = example@example.com, maximum = 255]`

		Optional:

			address=[
					street = `[string, maximum = 255]`
					suite = `[string, maximum = 55]`
					city = `[string, maximum = 55]`
					zipcode = `[string, maximum = 32]`
					geo=[
						lat = `[double, signed]`
						lng = `[double, signed]`
					]
				]
			phone = `[string, maximum = 55]`
			website = `[string, maximum = 255]`
			company = [
					name = `[string, maximum = 255]`
					catchPhrase = `[string, maximum = 255]`
					bs = `[string, maximum = 255]`
				]
				

* **Sucess Response** :

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

* **Error Response** :

		Code:401 BAD REQUEST 
		Content:{error:  the request was invalid, {field1, field2,...,fieldn} don't have the specified format.}

		Code:422 UNPROCESSABLE ENTITY
		Content:{error: {field1, field2,.., fieldn} are missing in the payload}

* **Sample Call** :

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

* **Notes** :

        id:[assigned by the service]

**LIST USERS**

List all users by filters and an order

* **URL** 	
		rest/v1/users

* **Method** 

		`GET`

* **URL Params** 

        Requiered:
	        offset = `[integer]`
	        limit = `[integer, default=20]`
            example: rest/v1/users?offset=0&limit=8

	    Optional:
            name_order = `[asc | des]`
            examples :
	    - by order ascendent  = rest/v1/users?offset=0&limit=8&name_order=asc  
	    - by order descendent = rest/v1/users?offset=0&limit=8&name_order=des 
            IDUser_order = `[asc | des]`
            examples :
	    - by order ascendent  = rest/v1/users?offset=0&limit=8&IDUser_order=asc  
	    - by order descendent = rest/v1/users?offset=0&limit=8&IDUser_order=des 
            name_filter = `[ = | %pattern%]`
            examples : 
            - by name that start with M = rest/v1/users?offset=0&limit=8&name_filter=%M% 
	    - by name that qual to nano = rest/v1/users?offset=0&limit=8&name_filter=nano 
	    username_filter = `[ = | %pattern%]`
            examples : 
            - by username that start with M = rest/v1/users?offset=0&limit=8user&name_filter=%M% 
	    - by username that equal to nano = rest/v1/users?offset=0&limit=8&username_filter=nano 
	    email_filter = `[ = | %pattern%]`
            examples : 
            - by email that start with M = rest/v1/users?offset=0&limit=8&email_filter=%M% 
	    - by email that qual to nano = rest/v1/users?offset=0&limit=8&email_filter=nano 
	    website_filter = `[ = | %pattern%]`
            examples : 
            - by website that start with M = rest/v1/users?offset=0&limit=8&website_filter=%M% 
	    - by website that equal to nano = rest/v1/users?offset=0&limit=8&website_filter=nano 
	    company_name_filter = `[ = | %pattern%]`
            examples : 
            - by company_name that start with M = rest/v1/users?offset=0&limit=8&company_name_filter=%M% 
	    - by company_name  that equal to nano = rest/v1/users?offset=0&limit=8&company_filter=nano 
            
* **Data Params** 
        
	None

* **Sucess Response** :

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
 * **Error Response** :
 
           	Code:401 BAD REQUEST 
		    Content:{error:  the request was invalid, {field1, field2,...,fieldn} don't have the specified format.}

  * **Sample Call** *:
  
            $.ajax({
                url: "/albums",
                dataType: "json",
                type : "GET",
                success : function(r) {
                    console.log(r);
                }
            });

        *Notes:

**UPDATE USERS**

Update a single user

* **URL** 	

		rest/v1/users/:userId

* **Method** 

		`PUT`

* **URL Params** 

		userId=`[integer, not editable]`

		Optional:
			None

* **Data Params** 
		
		Required:

			name=´[string, maximum = 255]´
			username=´[string, unique, maximum = 55]´
			email=´[string, format_validation = example@example.com, maximum = 255]´

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

* **Sucess Response** :

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
			    "msg": "User updated correctly"
		  	 }
		]

* **Error Response** :
		
		Code:401 BAD REQUEST 
		Content:{error:  the request was invalid, {field1, field2,...,fieldn} don't have the specified format.}

		Code:422 UNPROCESSABLE ENTITY
		Content:{error: {field1, field2,.., fieldn} are missing in the payload}

* **Sample Call** :

		$.ajax({
		    url: "/users/:6",
		    dataType: "json",
		    type : "PUT",
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

* **Notes** :

        	id:[assigned by the service]
	
**DELETE USERS**

Delete a single user

* **URL	** 

		rest/v1/users/:userId

* **Method** 

		´DELETE´

* **URL Params** 

		Required
			id=`[integer, not editable]`
		Optional:
			None
* **Data Params** 
		
        	Required:
			None		
		Optional:
			None

* **Sucess Response** :

		Code:204
		Content: [ 
				"msg": "User delete correctly"
		]

* **Error Response ** :
		
		Code:401 BAD REQUEST 
		Content:{error:  the request was invalid, userId doesn't exist.}



* **Sample Call** :

		$.ajax({
		    url: "/users/:5",
		    dataType: "json",
		    type : "DELETE",
		    success : function(r) {
		     	console.log(r);
		    }
	  	});

* **Notes** :
