## Users

<!-------------------- LIST USERS -------------------->

### List users

`GET /users`

```json
{
  "data":[{
    "id": "e83540c7-75a0-4715-96dc-c10a364e0390",
    "userName": "habsgoalie123",
    "firstName": "Carey",
    "lastName": "Price",
    "email": "gohabsgo@cloud.ca",
    "createdDate": 1476796926000,
    "status": "ACTIVE",
    "organization": {
      "id": "8e3393ce-ee63-4f32-9e0f-7b0200fa655a",
      "name": "Canadiens"
    },
    "roles": [
      {
        "id": "cdaaa9d0-304e-4063-b1ab-de31905bdab8",
        "name": "End-User"
      },
      {
        "id": "fe6d2614-3c33-447c-96f2-c79f67f5fd19",
        "name": "Environment Admin",
        "environment": {
          "id": "afcafd98-0287-4139-bb77-f29ab0549eaa"
        }
      }
    ]
  }]
}
```
Retrieve information about a users you have accessed to. If you want access to other users in your [organization or sub-organizations](#organizations), you will need to be assigned a [role](#Roles) with the `View existing users` permission. Without this permission, you will only be see your own user in the list.

Attributes | &nbsp;
---------- | -----------
`id`<br/>*UUID* | ---
`userName`<br/>*string* | The username of the user
`firstName`<br/>*string* | The first name of the user
`lastName`<br/>*string* | The last name of the user
`email`<br/>*string* | The email of the user
`createdDate`<br/>*long* | The date in [unix time](#https://en.wikipedia.org/wiki/Unix_time) that the user was created
`status`<br/>*string* | The current status of the user.
`organization`<br/>*[Organization](#organization)* | The organization to which the user belongs
`roles`<br/>*Array[[Role](#roles)]* | The system and environments roles that are assigned to the user<br/>*includes*: `id`, `name` and `environment.id`


<!-------------------- GET USER -------------------->

### Get user

`GET /users/:id`

```json
{
  "data":{
    "id": "fdf60a19-980d-4380-acab-914485111305",
    "userName": "frodo",
    "firstName": "Frodo",
    "lastName": "Baggins",
    "email": "frodo@cloud.ca",
    "createdDate": 1476796926000,
    "status": "ACTIVE",
    "organization": {
      "id": "c64dcd1d-9123-45e5-ad00-5d635c49176b",
      "name": "The Shire"
    },
    "environments": [{
      "id": "55724a36-4817-4cd3-927e-57d8a8b41eb8",
      "name": "hobbiton"
    }],
    "roles": [
      {
        "id": "5f0a4f20-3537-4bcd-81fe-2b74fd4c07e0",
        "name": "End-User"
      },
      {
        "id": "0b9159cd-81ac-48d1-be8a-7595a1617c94",
        "name": "Read-Only",
        "environment": {
          "id": "55724a36-4817-4cd3-927e-57d8a8b41eb8"
        }
      }
    ]
  }
}
```
Retrieve information about a specific user. If you want access to other users in your [organization or sub-organizations](#organizations), you will need to be assigned a [role](#Roles) with the `View existing users` permission.

Attributes | &nbsp;
---------- | -----------
`id`<br/>*UUID* | ---
`userName`<br/>*string* | The username of the user
`firstName`<br/>*string* | The first name of the user
`lastName`<br/>*string* | The last name of the user
`email`<br/>*string* | The email of the user
`createdDate`<br/>*long* | The date in [unix time](#https://en.wikipedia.org/wiki/Unix_time) that the user was created
`status`<br/>*string* | The current status of the user.
`organization`<br/>*[Organization](#organization)* | The organization to which the user belongs
`environments`<br/>*Array[[Environment](#environments)]* | The environments the user is member of<br/>*includes*: `id`, `name`
`roles`<br/>*Array[[Role](#roles)]* | The system and environments roles that are assigned to the user<br/>*includes*: `id`, `name` and `environment.id`


<!-------------------- CREATE USER -------------------->


### Create user

`POST /users`

> Request example

```json
{
  "userName": "vader42",
  "firstName": "Anakin",
  "lastName": "Skywalker",
  "email": "vader42@cloud.ca",
  "organization": {
    "id": "645cf4ce-3699-40c5-a1a8-0b3e945f49ee"
  },
  "roles": [
    {
      "id": "dd01c908-371c-4ec5-9fd7-80b1bfac8975"
    }
  ]
}
```

Create a user in a specific organization. There's two different types of [role](#roles) you can assign to the user. A system role will determine the set of system permissions the user will have. An environment role will give the user access to an environment and will determine what he can see and do in that environment. You will need a [role](#roles) with the `Create a new user` permission to execute this operation.

<!-- On successful creation of the user, he will receive an email to -->

Required | &nbsp;
-------- | -----------
`userName`<br/>*string* | Username of the new user. Should be unique across the organization.
`firstName`<br/>*string* | First name of the user
`lastName`<br/>*string* | Last name of the user
`email`<br/>*string* | Email of the user. Should be unique across the organization.

Optional | &nbsp;
-------- | -----------
`organization`</br>*[Organization](#organization)* | Organization in which the user will be created. *Defaults to your organization*<br/>*required:* `id`
`roles`<br/>*Array[[Role](#roles)]* | The system and environment roles to give to the user<br/>*required*: `id`


<!-------------------- UPDATE USER -------------------->


### Update user

`PUT /users/:id`

```json
{
  "userName": "spidey1",
  "firstName": "Peter",
  "lastName": "Parker",
  "email": "spidey1@cloud.ca",
  "roles": [
    {
      "id": "dd01c908-371c-4ec5-9fd7-80b1bfac8975"
    }
  ]
}
```

Update a specific user. It is important to note that updating the list of roles will override the previous one. You will need a [role](#roles) with the `Users update` permission to execute this operation.

Optional | &nbsp;
-------- | -----------
`userName`<br/>*string* | The new username of the user. Should be unique across the organization.
`firstName`<br/>*string* | The new first name of the user
`lastName`<br/>*string* | The new last name of the user
`email`<br/>*string* | The new email of the user. Should be unique across the organization.
`roles`<br/>*Array[[Role](#roles)]* | The new list of system or environment roles to give to the user. This will override the previous list of roles.<br/>*required*: `id`



<!-------------------- DELETE USER -------------------->


### Delete user

`DELETE /users/:id`

Delete a specific user. You will need a [role](#roles) with the `Delete an existing user` permission to execute this operation.


<!-------------------- UNLOCK USER -------------------->


### Unlock user

`POST /users/:id/unlock`

A user with 10 consecutive unsuccessful logins will be automatically locked by our system. This API can be used to unlock a user in this situation.
