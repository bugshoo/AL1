API REST - Resource Management Specification

Users

URL

    /rest/v1/										Endpoint version 1.0

API CALLS

    POST    /rest/v1/users/add/name=:name&username=:username&email=:email			Create a user
    GET     /rest/v1/users?id=:id								Show a user 
    PUT     /rest/v1/users?id=:id&name=:name&...						Update a user
    DELETE  /rest/v1/users?id=:id								Delete a user
    
    
DOCUMENTATION

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
	Content: { error : "" }
	
SIMPLE CALL

$ curl 'http://endpoint/rest/v1/users/add/name=gabriel&username=gabo&email=gbortega@gmail.com'

NOTES

<This is where all uncertainties, commentary, discussion etc. can go. I recommend timestamping and identifying oneself 
