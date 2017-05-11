# API user's especifications

## Detail especifications
  | Method       |Endpoint          |  Description |
  |:------------:|------------------|:------------:|
  |`GET`         |/api/v1/users     |              |
  |`GET`         |/api/v1/users/:id |              |
  |`POST`        |/api/v1/users     |              |
  |`PUT`         |/api/v1/users     |              |
  |`DELETE`      |/api/v1/users/:id |              |
  


## Data params' description

### users

  | Field name   |      Type      |  Description | Required |
  |:------------:|:--------------:|:------------:|:--------:|
  |id            |[integer]       |              |          |
  |name          |[string]        |255           |true      |
  |username      |[string]        |55            |true      |
  |email         |[string]        |255           |true      |
  |address       |[address]       |              |false     |
  |phone         |[string]        |55            |true      |
  |website       |[string]        |255           |false     |
  |company       |[company]       |              |true      |
  
### address(subfield)   

  | Field name   |      Type      |  Description | Required |
  |:------------:|:--------------:|:------------:|:--------:|
  |street        |[string]        |255           |false     |
  |suit          |[string]        |55            |false     |
  |city          |[string]        |55            |false     |
  |zipcode       |[string]        |32            |false     |
  |geo           |[geo]           |              |false     |
  
  
### geo(subfield) 

  | Field name   |      Type      |  Description | Required |
  |:------------:|:--------------:|:------------:|:--------:|
  |lat           |[double signed] |              | false    |
  |lng           |[double signed] |              | false    |
  
  
### company(subfield)

  | Field name   |      Type      |  Description | Required |
  |:------------:|:--------------:|:------------:|:--------:|
  |name          |[string]        |255           | false    |
  |catchPhrase   |[string]        |55            | false    |
  |bs            |[string]        |255           | false    |
  

**List Users**
----
  Returns json data about all the users.

* **URL**

  /api/v1/users

* **Method:**

  `GET`
  
* **URL Params**

  
  - Paginations
  
   /api/v1/users?count=[integer]&page[integer]

    | Endpoint                   |  Description                              |
    |:--------------------------:|:-----------------------------------------:|
    |/api/v1/users?count=5&page=2| Return the second ones 5 users' records   |
    |/api/v1/users?count=7&page=5| Return the fifth ones 7 users' records    |
    
  - Ordering
  
  /api/v1/users?sort={ | -} {name | id}

    | Endpoint                   |  Description                              |
    |:--------------------------:|:-----------------------------------------:|
    |/api/v1/users?sort=-name    | Return the descendent users's list by name|
    |/api/v1/users?sort=name     | Return the ascendent users's list by name |
    |/api/v1/users?sort=id       | Return the ascendent users's list by id   |
    |/api/v1/users?sort=-id      | Return the ascendent users's list by id   |
    

  - Filtering
  
  /api/v1/users?filter={name | username | email | website | company}&value=[string]
   
    | Endpoint                                         |  Description                                                     |
    |:------------------------------------------------:|:----------------------------------------------------------------:|
    |/api/v1/users?filter=username&value=jeffer,like   | Return  users' records with username like %jeffer%               |
    |/api/v1/users?filter=email&value=jeffer,eq        | Return  user record with email jhon.pantoja@correounivalle.edu.co   |


* **Data Params**

  None

* **Success Response:**

  * **Code:** `200` <br />
    **Content:** 
 ```javascript
[
  {
    id: 1,
    name: "Leanne Graham",
    username: "Bret",
    email: "Sincere@april.biz",
    address: {
      street: "Kulas Light",
      suite: "Apt. 556",
      city: "Gwenborough",
      zipcode: "92998-3874",
      geo: {
        lat: "-37.3159",
        lng: "81.1496"
      }
    },
    phone: "1-770-736-8031 x56442",
    website: "hildegard.org",
    company: {
      name: "Romaguera-Crona",
      catchPhrase: "Multi-layered client-server neural-net",
      bs: "harness real-time e-markets"
    }
  },
  {
    id: 2,
    name: "Ervin Howell",
    username: "Antonette",
    email: "Shanna@melissa.tv",
    address: {
      street: "Victor Plains",
      suite: "Suite 879",
      city: "Wisokyburgh",
      zipcode: "90566-7771",
      geo: {
        lat: "-43.9509",
        lng: "-34.4618"
      }
    },
    phone: "010-692-6593 x09125",
    website: "anastasia.net",
    company: {
      name: "Deckow-Crist",
      catchPhrase: "Proactive didactic contingency",
      bs: "synergize scalable supply-chains"
    }
  }
]
```
 
* **Error Response:**

  None

* **Sample Call:**

  ```javascript
    $.ajax({
      url: "/api/v1/users",
      dataType: "json",
      type : "GET",
      success : function(r) {
        console.log(r);
      }
    });
  ```
  
**Show Photos**
----
  Returns json data about a single user.

* **URL**

  /api/v1/users/:id

* **Method:**

  `GET`
  
*  **URL Params**

  | Field name   |      Type      |  Description | Require |
  |:------------:|:--------------:|:------------:|:-------:|
  |id            |Integer         |              | true    |


* **Data Params**

  None

* **Success Response:**

  Returns JSON representation of user 
  
  **Code:** `STATUS 200` <br />
  **Content:**
     
```javascript
 
 Code: 200
 Content:

  {
    id: 1,
    name: "Leanne Graham",
    username: "Bret",
    email: "Sincere@april.biz",
    address: {
      street: "Kulas Light",
      suite: "Apt. 556",
      city: "Gwenborough",
      zipcode: "92998-3874",
      geo: {
        lat: "-37.3159",
        lng: "81.1496"
      }
    },
    phone: "1-770-736-8031 x56442",
    website: "hildegard.org",
    company: {
      name: "Romaguera-Crona",
      catchPhrase: "Multi-layered client-server neural-net",
      bs: "harness real-time e-markets"
    }
  }

```
 
* **Error Response:**

  * **Code:** 404 NOT FOUND <br />
    **Content:** `{ error : "This user doesn't exist" }`

* **Sample Call:**

  ```javascript
    $.ajax({
      url: "/api/v1/users/1",
      dataType: "json",
      type : "GET",
      success : function(r) {
        console.log(r);
      }
    });
  ```
**Create photo**
----
  Create a new user and returns json data about a user created.

* **URL**

  /api/v1/users

* **Method:**

  `POST`
  
*  **URL Params**
  
  None

* **Data Params**

   See definition in Data params' description


*  *Example:*
    
```javascript

  {
    name: "Leanne Graham",
    username: "Bret",
    email: "Sincere@april.biz",
    address: {
      street: "Kulas Light",
      suite: "Apt. 556",
      city: "Gwenborough",
      zipcode: "92998-3874",
      geo: {
        lat: "-37.3159",
        lng: "81.1496"
      }
    },
    phone: "1-770-736-8031 x56442",
    website: "hildegard.org",
    company: {
      name: "Romaguera-Crona",
      catchPhrase: "Multi-layered client-server neural-net",
      bs: "harness real-time e-markets"
    }
  }

```

* **Success Response:**

  * **Code:** `201` <br />
    **Content:** 
```javascript

  {
    id: 1,
    name: "Leanne Graham",
    username: "Bret",
    email: "Sincere@april.biz",
    address: {
      street: "Kulas Light",
      suite: "Apt. 556",
      city: "Gwenborough",
      zipcode: "92998-3874",
      geo: {
        lat: "-37.3159",
        lng: "81.1496"
      }
    },
    phone: "1-770-736-8031 x56442",
    website: "hildegard.org",
    company: {
      name: "Romaguera-Crona",
      catchPhrase: "Multi-layered client-server neural-net",
      bs: "harness real-time e-markets"
    }
  }

```
 
* **Error Response:**

  * **Code:** 400 BAD REQUEST <br />
    **Content:** `{ error : "some property was not provided or the value is too long" }`

* **Sample Call:**

  ```javascript
    $.ajax({
      url: "/api/v1/users",
      dataType: "json",
      data: {
                name: "Leanne Graham",
                username: "Bret",
                email: "Sincere@april.biz",
                address: {
                  street: "Kulas Light",
                  suite: "Apt. 556",
                  city: "Gwenborough",
                  zipcode: "92998-3874",
                  geo: {
                    lat: "-37.3159",
                    lng: "81.1496"
                  }
                },
                phone: "1-770-736-8031 x56442",
                website: "hildegard.org",
                company: {
                  name: "Romaguera-Crona",
                  catchPhrase: "Multi-layered client-server neural-net",
                  bs: "harness real-time e-markets"
                }
              },
      type : "POST",
      success : function(r) {
        console.log(r);
      }
    });
  ```
  
**Edit photo**
----
  Update a user and returns json data about a user updated.

* **URL**

  /api/v1/users

* **Method:**

  `PUT`
  
*  **URL Params**
  
  None

* **Data Params**

   See definition in Data params' description


*  *Example:*
    
```javascript

  {
      id: 2,
      name: "Ervin Howell",
      username: "Antonette",
      email: "Shanna@melissa.tv",
      address: {
        street: "Victor Plains",
        suite: "Suite 879",
        city: "Wisokyburgh",
        zipcode: "90566-7771",
        geo: {
          lat: "-43.9509",
          lng: "-34.4618"
        }
      },
      phone: "010-692-6593 x09125",
      website: "anastasia.net",
      company: {
        name: "Deckow-Crist",
        catchPhrase: "Proactive didactic contingency",
        bs: "synergize scalable supply-chains"
      }
  }

```

* **Success Response:**

  * **Code:** `200` <br />
    **Content:** 
```javascript

  {
    id: 2,
    name: "Ervin Howell",
    username: "Antonette",
    email: "Shanna@melissa.tv",
    address: {
      street: "Victor Plains",
      suite: "Suite 879",
      city: "Wisokyburgh",
      zipcode: "90566-7771",
      geo: {
        lat: "-43.9509",
        lng: "-34.4618"
      }
    },
    phone: "010-692-6593 x09125",
    website: "anastasia.net",
    company: {
      name: "Deckow-Crist",
      catchPhrase: "Proactive didactic contingency",
      bs: "synergize scalable supply-chains"
    }
  }

```
 
* **Error Response:**

  * **Code:** 400 BAD REQUEST <br />
    **Content:** `{ error : "some property was not provided or the value is too long" }`
    
  * **Code:** 404 NOT FOUND <br />
    **Content:** `{ error : "This user doesn't exist" }`

* **Sample Call:**

  ```javascript
    $.ajax({
      url: "/api/v1/users",
      dataType: "json",
      data: {
                id: 2,
                name: "Ervin Howell",
                username: "Antonette",
                email: "Shanna@melissa.tv",
                address: {
                  street: "Victor Plains",
                  suite: "Suite 879",
                  city: "Wisokyburgh",
                  zipcode: "90566-7771",
                  geo: {
                    lat: "-43.9509",
                    lng: "-34.4618"
                  }
                },
                phone: "010-692-6593 x09125",
                website: "anastasia.net",
                company: {
                  name: "Deckow-Crist",
                  catchPhrase: "Proactive didactic contingency",
                  bs: "synergize scalable supply-chains"
                }
              },
      type : "PUT",
      success : function(r) {
        console.log(r);
      }
    });
  ```


**Delete photo**
----
  Returns json data about a deleted user.

* **URL**

  /api/v1/users/:id

* **Method:**

  `DELETE`
  
*  **URL Params**
  
    | Field name   |      Type      |  Description | Require |
    |:------------:|:--------------:|:------------:|:-------:|
    |id            |Integer         |              | true    |


* **Data Params**

  None
  
* **Success Response:**

  * **Code:** `200`  <br />
    **Content:** `{message: "The user was successfully removed"}`
     
* **Error Response:**
    
   * **Code:** `404` NOT FOUND <br />
       **Content:** `{ error : "This user doesn't exist" }`

* **Sample Call:**

  ```javascript
    $.ajax({
      url: "/api/v1/users/1",
      dataType: "json",
      type : "DELETE",
      success : function(r) {
        console.log(r);
      }
    });
  ```