API REST - Resource Management Specification

URL

    /rest/v1/										Endpoint version 1.0

Users

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



METHOD
POST
 
URL PARAMS

REQUIRED
	
	body

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

default                                        operacion exitosa
                                

ERROR RESPONSE
 	405                                                entrada invalida

----------------------------------------------------------------------------------------------------------------



METHOD
PUT                                                  

Actualiza un usuario existente
 
URL PARAMS

REQUIRED
	
	body

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

default                                        operacion exitosa
                                

ERROR RESPONSE
 	
400                                   id invalido

404                                      usuario no encontrado

405                                     excepcion de validacion

