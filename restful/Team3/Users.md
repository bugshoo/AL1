API REST - Resource Management Specification
Documentation
Version: 1.0
Resource: Users


    
TITLE
Create a user

URL
/rest/v1/users

METHOD
GET

URL PARAMS

REQUIRED
	
	name: 		[string 255],
	username: 	[string 55],
	email: 		[string 255]

OPTIONAL

	phone:		[string 55],  	 
	website:	[string 255]


DATA PARAMS

{u: {
	id: 	  [integer],
	name:     [string],
	username: [string],
	email:    [string],
	address:
	{	street: [string],
        	suite: [string],
        	city: [string],
        	zipcode: [string]
	}
        	geo:
		{
            		lat: [double signed].,
            		lng: [double signed]
		{
	phone:   [string],
	website: [string],
        company:
	{
	        name: 		[string],
	        catchPhrase:	[string],	
	        bs: 		[string]
	}
}

SUCCESS RESPONSE

Example:
	Code: 200
	Content: { OK }

ERROR RESPONSE
 	Code: 400
	Content: { error : "Bad request" }
	
SIMPLE CALL

$ curl 'http://IP-SERVER:PORT/rest/v1/users/add/name=gabriel&username=gabo&email=gbortega@gmail.com'

NOTES

<This is where all uncertainties, commentary, discussion etc. can go. I recommend timestamping and identifying oneself 
