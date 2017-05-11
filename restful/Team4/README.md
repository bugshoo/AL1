
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



		