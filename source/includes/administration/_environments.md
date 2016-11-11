## Environments

<!-------------------- LIST ENVIRONMENTS -------------------->

### List environments

`GET /environments`

```json
{
  "data": [{
    "id": "1ee5cd43-8395-4cd5-a20f-0f1e83b7f8bd",
    "name": "cheyenne_mountain",
    "description": "Environment for base at Cheyenne Mountain",
    "membership": "MANY_USERS",
    "creationDate": 1474986518000,
    "organization": {
      "id": "a9f93785-0545-4876-8241-3b19b9a86721",
      "name": "sg1",
      "entryPoint": "sg1"
    },
    "serviceConnection": {
      "id": "7f0fa906-490a-467b-bc44-e2382d43015e",
      "name": "compute"
    },
    "roles": [{
      "id": "951b768b-e91c-4d20-8b52-d4a2ab5a538a",
      "name": "Environment Admin",
      "isDefault": true,
      "users": [{
        "id": "9f84a6ce-7be1-4a08-a25b-edc6e57fb7e3",
        "name": "jack_oneill"
      }]
    }]
  }]
}
```

Attributes | &nbsp;
---------- | -----------
`id`<br/>*UUID* | ---
`name`<br/>*string* | The name of the environment
`description`<br/>*string* | The description of the environment
`membership`<br/>*string* | ---
`creationDate`<br/>*long* | The date in [unix time](#https://en.wikipedia.org/wiki/Unix_time) that the environment was created
`organization`<br/>*[Organization](#organizations)* | The organization of the environment<br/>*includes*: `id`, `name`, `entryPoint`
`serviceConnection`<br/>*[ServiceConnection](#serviceConnections)* | The service connection of the environment<br/>*includes*: `id`, `name`
`roles`<br/>*Array[[Role](#roles)]* | The roles of the environment with all the users assigned to them.<br/>*includes*: `id`, `name`, `isDefault`, `users.id`, `users.name`


You will need a [role](#roles) with the `Environments read` permission to execute this operation.


<!-------------------- GET ENVIRONMENT -------------------->

### Get environment

`GET /environments/:id`

```json
{
  "data": {
    "id": "487a2745-bb8a-44bc-adb1-e3b048f6def2",
    "name": "galactica",
    "description": "Environment for the Galactica",
    "membership": "MANY_USERS",
    "creationDate": 1474986518000,
    "organization": {
      "id": "a3340a89-8f60-407d-8a49-f5cfe81eef8f",
      "name": "kobol",
      "entryPoint": "kobol"
    },
    "serviceConnection": {
      "id": "7f0fa906-490a-467b-bc44-e2382d43015e",
      "name": "compute"
    },
    "users": [{
      "id": "6e84ab70-4c62-4db1-bbd8-343636a34647",
      "userName": "starbuck",
    }],
    "roles": [{
      "id": "b04b8a7c-6e89-4dba-9734-74d9f1b7be04",
      "name": "Environment Admin",
      "isDefault": true,
      "users": [{
        "id": "6e84ab70-4c62-4db1-bbd8-343636a34647",
        "name": "starbuck"
      }]
    }]
  }
}
```

Attributes | &nbsp;
---------- | -----------
`id`<br/>*UUID* | ---
`name`<br/>*string* | The name of the environment
`description`<br/>*string* | The description of the environment
`membership`<br/>*string* | ---
`creationDate`<br/>*long* | The date in [unix time](#https://en.wikipedia.org/wiki/Unix_time) that the environment was created
`organization`<br/>*[Organization](#organizations)* | The organization of the environment<br/>*includes*: `id`, `name`, `entryPoint`
`serviceConnection`<br/>*[ServiceConnection](#serviceConnections)* | The service connection of the environment<br/>*includes*: `id`, `name`
`users`<br/>*Array[[User](#users)]* | The users that are members of the environment<br/>*includes*: `id`, `username`
`roles`<br/>*Array[[Role](#roles)]* | The roles of the environment with all the users assigned to them.<br/>*includes*: `id`, `name`, `isDefault`, `users.id`, `users.name`


You will need a [role](#roles) with the `Environments read` permission to execute this operation.


<!-------------------- CREATE ENVIRONMENT -------------------->


### Create environment

`POST /environments`]

```json
{
  "name": "glados",
  "description": "Environment property of Aperture Science",
  "membership": "MANY_USERS",
  "organization": {
    "id": "2fd60d6f-1fee-4fe5-8ec6-46d8776acc6f"
  },
  "serviceConnection": {
    "id": "7f0fa906-490a-467b-bc44-e2382d43015e"
  },
  "roles": [{
    "name": "Environment Admin",
    "isDefault": true,
    "users": [{
      "id": "73b17dab-1705-45f1-84e2-997e2af5641b"
    }]
  }]
}
```


Required | &nbsp;
-------- | -----------
`name`<br/>*string* | The name of the new environment. Should be unique in the environment and only contain lower case characters, numbers, dashes and underscores.
`description`<br/>*string* | The description of the new environment.
`serviceConnection`<br/>*[ServiceConnection](#serviceConnections)* | The service connection that the environment should be created in<br/>*required*: `id`

Optional | &nbsp;
-------- | -----------
`organization`<br/>*[Organization](#organizations)* | The organization that the environment should be created in. *Defaults to your organization*<br/>*required*: `id`
`membership`<br/>*string* | ---
`roles`<br/>*Array[[Role](#roles)]* | The roles of the environment and the users assigned to them. Also, defines the default role of the environment.<br/>*required*: `name`, `users.id`<br/>*optional*: `isDefault`


You will need a [role](#roles) with the `Environments create` permission to execute this operation.


<!-------------------- UPDATE ENVIRONMENT -------------------->


### Update environment

`PUT /environments/:id`

```json
{
  "name": "skynet-beta",
  "description": "Environment for the Skynet project",
  "roles": [{
    "id": "f9dea588-d7ab-4f42-b6e6-4b85f273f3db",
    "users": [{
      "id": "07e02355-d05b-47cf-860d-f69cf0432276"
    }]
  }]
}
```


Optional | &nbsp;
-------- | -----------
`name`<br/>*string* | The updated name of the environment. Should be unique in the environment and only contain lower case characters, numbers, dashes and underscores.
`description`<br/>*string* | The updated description of the environment
`membership`<br/>*string* | ---
`roles`<br/>*Array[[Role](#roles)]* | Update the users roles in the environment. Also, can also update the default role.<br/>*required*: `name`, `users.id`<br/>*optional*: `isDefault`


You will need a [role](#roles) with the `Environments update` permission to execute this operation.

<!-------------------- DELETE ENVIRONMENT -------------------->


### Delete environment

`DELETE /environments/:id`

Delete a specific environment. **Be careful: This will destroy all the resources in your environment.** You will need a [role](#roles) with the `Delete an existing environment	` permission to execute this operation.
