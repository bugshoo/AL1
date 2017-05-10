# Users

- Fields:
```
    id: integer
    name: string 255
    username: string 55
    email: string 255
    address:
        street: string 255
        suite: string 55
        city: string 55
        zipcode: string 32
        geo:
            lat: double signed
            lng: double signed
    phone: string 55
    website: string 255
    company:
      name: string 255
      catchPhrase: string 255
      bs: string 255
```
- Identifier:

            id (assigned/non editable)

- Mandatory:

            name
            username (unique)
            email (format validation)

- Lists:

    + Pagination required (default paging 20 items)
    
    + Ordering by:

            id (default) (asc | desc)  
            name (asc | desc)  

    + Filtering by:

            name (equal | like)  
            username (equal | like)  
            email (equal | like)  
            website (equal | like)  
            company.name (equal | like)  
        
    + Total counts



# Posts

- Fields:
```
    userId: integer
    id: integer
    title: string 255
    body: string 65535
```

- Identifier:

            id (assigned/non editable)

- Mandatory:

            userId (Related to users.id)
            title

- Lists:

    + Pagination required (default paging 20)

    + Ordering by:

            id (default) (asc | desc)
            title (asc | desc)
 
    + Filtering by:
    
            userId (equal)
            title (equal | like)
            
    + Total counts



# Comments

- Fields:
```
    postId: integer
    id: integer
    name: string 255
    email: string 255
    body: string 65535
```

- Identifier:

            id (assigned/non editable)

- Mandatory:

            postId (Related to posts.id)
            name
            email (format validation)

- Lists:

    + Pagination required (default paging 30)

    + Ordering by:

            name (asc | desc)

    + Filtering by:

            postId (equal)
            name (equal | like)

    + Total counts



# Albums

- Fields:
```
    userId: integer
    id: integer
    title: string 255
```

- Identifier:

            id (assigned/non editable)

- Mandatory:

            userId (Related to users.id)
            title

- Lists:

    + Pagination required (default paging 10)

    + Ordering by:

            name (asc | desc)

    + Filtering by:

            userId (equal)
            title (equal | like)

    + Total counts



# Photos

- Fields:
```
    albumId: integer
    id: integer
    title: string 255
    url: string 255
    thumbnailUrl: string 255
```

- Identifier:

            id (assigned/non editable)

- Mandatory:

            albumId (Related to albums.id)
            title
            url (format validation)
            thumbnailUrl (format validation)

- Lists:

    + Pagination required (default paging 25)

    + Ordering by:

            title (asc | desc)

    + Filtering by:

            albumId (equal)
            title (equal | like)

    + Total counts



# Todos

- Fields:
```
    userId: integer
    id: integer
    title: string 255
    completed: boolean
```

- Identifier:

            id (assigned/non editable)

- Mandatory:

            userId (Related to users.id)
            title
            completed

- Lists:

    + Pagination required (default paging 5)

    + Ordering by:

            title (asc | desc)

    + Filtering by:

            userId (equal)
            title (equal | like)
            completed (equal)

    + Total counts



