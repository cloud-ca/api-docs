## Service connections

Service connections are the services that you can create resources for (e.g. compute, object storage). [Environments](#environments) are created for a specific service which allows you to create and manage resources within that service.

<!---- The service APIs are documented [here](#serviceApis) ---->


<!-------------------- LIST ORGANIZATIONS -------------------->
### List service connections

`GET /services/connections`

```json
{
  "data":[{
    "id": "adfbdb51-493b-45b1-8802-3f6327afb9e6",
    "serviceCode": "compute-qc",
    "name": "Compute - Québec",
    "type": "CloudCA",
    "status": {  
      "lastUpdated": "2017-08-15T12:00:00.000Z",
      "reachable": true
    }
  }]
}
```
```go
ccaClient := cca.NewCcaClient("your_api_key")
serviceConnection, err := ccaClient.ServiceConnections.List()
```

Attributes | &nbsp;
---- | -----------
`id`<br/>*UUID* | The id of the service connection
`serviceCode`<br/>*string* | The service code of the service connection. It is used in the endpoint of the services API.
`name`<br/>*string* | The name of the service connection
`type`<br/>*string* | The type of the service connection.
`status`<br/>*Object* | Status of the service connection. Tells you if the service is up.<br/>*includes*: `lastUpdated`, `reachable`


<!-------------------- GET ORGANIZATION -------------------->

### Retrieve a service connection

`GET /services/connections/:id`

```json
{
  "data":[{
    "id": "adfbdb51-493b-45b1-8802-3f6327afb9e6",
    "serviceCode": "compute-qc",
    "name": "Compute - Québec",
    "type": "CloudCA",
    "status": {  
      "lastUpdated": "2017-08-15T12:00:00.000Z",
      "reachable": true
    }
  }]
}
```
```go
ccaClient := cca.NewCcaClient("your_api_key")
serviceConnections, err := ccaClient.ServiceConnections.Get("[service-connection-id]")
```

Attributes | &nbsp;
---- | -----------
`id`<br/>*UUID* | The id of the service connection
`serviceCode`<br/>*string* | The service code of the service connection. It is used in the endpoint of the services API.
`name`<br/>*string* | The name of the service connection
`type`<br/>*string* | The type of the service connection.
`status`<br/>*Object* | Status of the service connection. Tells you if the service is up.<br/>*includes*: `lastUpdated`, `reachable`
