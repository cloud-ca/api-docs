## Organizations
<!-------------------- LIST ORGANIZATIONS -------------------->
### List organizations

`GET /organizations`

> Response example

```json
{
   "data":[{
      "id": "03bc22bd-adc4-46b8-988d-afddc24c0cb5",
      "name": "Umbrella Corporation",
      "entryPoint": "umbrella",
      "parent": {
         "id": "8e3393ce-ee63-4f32-9e0f-7b0200fa655a",
         "name": "Canadiens"
      },
      "environments": [
         {
           "id": "9df14056-51e2-4000-ab14-beeaa488500d"
         }
      ],
      "roles": [
         {
           "id": "cdaaa9d0-304e-4063-b1ab-de31905bdab8"
         }
      ],
      "serviceConnections":[
         {
            "id":"11607a49-9691-40fe-8022-2e148bc0d720",
            "serviceCode":"compute-qc"
         }
      ]
  }]
}
```
Bacon ipsum dolor amet doner shoulder pig pancetta ribeye short loin tail spare ribs venison salami ground round jowl t-bone pastrami.Tri-tip pork biltong hamburger, short loin shankle kevin sausage picanha. Yada yada need body

Attributes | &nbsp;
---- | -----------
`id`<br/>*UUID* | The ID of the organization
`name`<br/>*string* | The organization name
`entryPoint`<br/>*string* | The entry point of the organization is the subdomain of the organization in the cloud.ca URL: [entryPoint].cloud.ca
`lastName`<br/>*string* | The last name of the user
`email`<br/>*string* | The email of the user
`createdDate`<br/>*long* |
`status`<br/>*string* | The current status of the user.
`organization`<br/>*[Organization](#organization)* | The organization to which the user belongs
`roles`<br/>*Array[[Role](#roles)]* | The system and environments roles that are assigned to the user<br/>*includes*: `id`, `name` and `environment.id`



<!-------------------- FIND ORGANIZATION -------------------->

### Get organization

`GET /organizations/:id`

> Response example

```json
{

}
```
Bacon ipsum dolor amet doner shoulder pig pancetta ribeye short loin tail spare ribs venison salami ground round jowl t-bone pastrami.Tri-tip pork biltong hamburger, short loin shankle kevin sausage picanha. Yada yada need body. The id of the organization to update


<!-------------------- CREATE ORGANIZATION -------------------->

### Create organization

`POST /organizations`

> Request example

```json
{
   "entryPoint":"umbrella",
   "name":"Umbrella Corp",
   "serviceConnections":[
      {
         "id":"9acb3b76-d5d0-420c-b075-ef320b7e5a3e"
      }
   ],
   "parent" : {
      "id":"bc0ceecf-feb5-412c-ab6e-a8df8eb7fbbd"
   }
}
```

Bacon ipsum dolor amet doner shoulder pig pancetta ribeye short loin tail spare ribs venison salami ground round jowl t-bone pastrami.Tri-tip pork biltong hamburger, short loin shankle kevin sausage picanha. Yada yada need body. The id of the organization to update

Required | &nbsp; | &nbsp;
---- | ---- | -----------
`entryPoint` | string | The entry point is {entryPoint}.cloud.ca
`name` | string | The name of the organization. (Add info about restrictions)

Optional | &nbsp; | &nbsp;
---- | ---- | -----------
`serviceConnections` | Array[[ServiceConnection](#service-connection)] | A list of service connection with id field.
`parent` | [Organization](#organization) | the UUID of the parent organization
