## Organization
<!-------------------- LIST ORGANIZATIONS -------------------->
### List organizations

`GET /organizations`

> Response example

```json
{

}
```
Bacon ipsum dolor amet doner shoulder pig pancetta ribeye short loin tail spare ribs venison salami ground round jowl t-bone pastrami.Tri-tip pork biltong hamburger, short loin shankle kevin sausage picanha. Yada yada need body. The id of the organization to update


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

#### Required
Name | Type | Description
---- | ---- | -----------
`entryPoint` | string | The entry point is {entryPoint}.cloud.ca
`name` | string | The name of the organization. (Add info about restrictions)

#### Optional
Name | Type | Description
---- | ---- | -----------
`serviceConnections` | Array[[ServiceConnection](#service-connection)] | A list of service connection with id field.
`parent` | [Organization](#organization) | the UUID of the parent organization
