## Users

<!-------------------- LIST USERS -------------------->

### List users

`GET /users`

> User example

```json
{

}
```
Bacon ipsum dolor amet doner shoulder pig pancetta ribeye short loin tail spare ribs venison salami ground round jowl t-bone pastrami.Tri-tip pork biltong hamburger, short loin shankle kevin sausage picanha. Yada yada need body. The id of the organization to update


<!-------------------- FIND USER -------------------->

### Get user

`GET /users/:id`

> User example

```json
{

}
```
Bacon ipsum dolor amet doner shoulder pig pancetta ribeye short loin tail spare ribs venison salami ground round jowl t-bone pastrami.Tri-tip pork biltong hamburger, short loin shankle kevin sausage picanha. Yada yada need body. The id of the organization to update


<!-------------------- CREATE USER -------------------->


### Create user

`POST /users`

> User example

```json
{

}
```

Bacon ipsum dolor amet doner shoulder pig pancetta ribeye short loin tail spare ribs venison salami ground round jowl t-bone pastrami.Tri-tip pork biltong hamburger, short loin shankle kevin sausage picanha. Yada yada need body. The id of the organization to update

#### Required
Name | Type | Description
---- | ---- | -----------
`userName` | *string* | Username of the new user. Should be unique across the organization.
`firstName` | *string* | First name of the user
`lastName` | *string* | Last name of the user
`email` | *string* | Email of the user. Should be unique across the organization.


#### Optional
Name | Type | Description
---- | ---- | -----------
`organization` | *[Organization](#organization)* | ...
`roles` | *Array[[Role](#roles)]* | ...


<!-------------------- UPDATE USER -------------------->


### Update user

`PUT /users/:id`

> User example

```json
{

}
```

Bacon ipsum dolor amet doner shoulder pig pancetta ribeye short loin tail spare ribs venison salami ground round jowl t-bone pastrami.Tri-tip pork biltong hamburger, short loin shankle kevin sausage picanha. Yada yada need body. The id of the organization to update


<!-------------------- DELETE USER -------------------->


### Delete user

`DELETE /users/:id`

> User example

```json
{

}
```

Bacon ipsum dolor amet doner shoulder pig pancetta ribeye short loin tail spare ribs venison salami ground round jowl t-bone pastrami.Tri-tip pork biltong hamburger, short loin shankle kevin sausage picanha. Yada yada need body. The id of the organization to update


<!-------------------- UNLOCK USER -------------------->


### Unlock user

`POST /users/:id/unlock`

> User example

```json
{

}
```

Bacon ipsum dolor amet doner shoulder pig pancetta ribeye short loin tail spare ribs venison salami ground round jowl t-bone pastrami.Tri-tip pork biltong hamburger, short loin shankle kevin sausage picanha. Yada yada need body. The id of the organization to update
