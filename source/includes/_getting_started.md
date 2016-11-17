# Getting started

The cloud.ca API allows you to manage your environments and provision resources in a simple programmatic way using standard HTTP requests.

The API is  [RESTful](https://en.wikipedia.org/wiki/Representational_state_transfer). Responses, successful or not, are returned in [JSON](http://www.json.org/). Request bodies must be [JSON](http://www.json.org/), and should be made over SSL.

Current API version : `api.cloud.ca/v1`

We have also developed tools to help consume our APIs. If you use `go`, check out our [library](https://github.com/cloud-ca/go-cloudca). If you use Terraform, check out our [provider](https://github.com/cloud-ca/terraform-cloudca). NB: both are being actively developed, so there is still some functionality missing.

## Authentication
```go
import "github.com/cloud-ca/go-cloudca"
ccaClient := cca.NewCcaClient("[your-api-key]")
```

```shell
## To authenticate, add a header
## Make sure to replace `[your-api-key]` with your API key.
curl "https://api.cloud.ca/v1/organizations" \
   -H "MC-Api-Key: [your-api-key]"
```

```dart
provider "cloudca" {
    api_key = "${var.my_api_key}"
}
```

API endpoints are secured by the same role-based access control (RBAC) as the cloud.ca portal. To identify who is making the requests, it is required to add a header to your HTTP requests:

`MC-Api-Key: [your-api-key]`

<aside class="notice">
You must replace <code>[your-api-key]</code> with your personal API key.
</aside>

The API key is found from the API keys section under the user profile menu. If you don't see cloud.ca API keys section, contact your system administrator as you may not have the permission to see that section. **Your API key carries the same privileges as your cloud.ca account, so be sure to keep it secret**. If you think your API has been compromised, regenerate your API key from the API keys section.

## HTTP verbs
The cloud.ca API can be used by any tool that is fluent in HTTP. The appropriate HTTP method should be used depending on the desired action.

Verbs | Purpose
------ | -------
`GET` | Used to retrieve information about a resource.
`POST` | Used to create (or provision) a new resource or perform an operation on it.
`PUT` | Used to update a resource.
`DELETE` | Used to remove/delete a resource.

## Responses
### Success response
<!--
```json
{
  "data": [
    { "_comment" : "JSON representation of first object goes here" },
    { "_comment" : "JSON representation of second object goes here" }
  ],
  "metadata": {
    "pageSize": 2,
    "pageCurrent": 1,
    "recordCount": 2,
    "sortField": "templateName",
    "sortOrder": "ASC"
  }
}
```
-->
```json
{
  "data": [
    { "_comment" : "JSON representation of first object goes here" },
    { "_comment" : "JSON representation of second object goes here" }
  ]
}
```

When an API request is successful, the response body will contain the `data` field:

Attributes | &nbsp;
--- | ---
`data` | The data field contains the object requested by the API caller
<!--
`metadata` | The metadata is an optionally returned field containing paging and sorting information
-->

<aside class="notice">
If the response does <strong>not</strong> contain the "data" field, the request was <strong>not</strong> successful
</aside>

### Error response

```json
{
  "errors": [
    {
      "code": 2012,
      "message": "Cannot stop an instance that isn't in the running state",
      "context": {
        "id": "4534cc36-bc46-48bc-ac5c-3ee4e42f0a44",
        "currentState": "Stopped",
        "expectedStates": [
          "Running"
        ],
        "type": "instances"
      }
    }
  ]
}
```
```go
_, err := ccaResources.Volumes.Get("[some-volume-id]")
if err != nil {
   if errorResponse, ok := err.(api.CcaErrorResponse); ok {
      if errorResponse.StatusCode == api.NOT_FOUND {
         fmt.Println("Volume was not found")
      } else {
         //Can get more details from the CcaErrors
         fmt.Println(errorResponse.Errors)
      }
   } else {
      //handle unexpected error
      panic("Unexpected error")
   }
}
```

When an API request is unsuccessful, the response body will contain the `errors` field :

Attributes | &nbsp;
--- | ---
`errors` | A list of errors objects that contain information about each error

Each error has additional fields to describe it :

Attributes | &nbsp;
--- | ---
`code` | The cloud.ca error code
`message` | A human readable explanation of the error code
`context` | Additional information

The HTTP status codes of error responses :

Status code | Reason
----------- | -------
`200` | The request was successful.
`204` | The request was successful and the response body is empty
`400` | Bad request -- Occurs when invalid parameters are provided or when quota limit is exceeded.
`403` | Forbidden -- Not authorized to perform this request.
`404` | Not Found -- Cannot locate the specified endpoint.
`405` | Method not allowed -- Cannot use that HTTP verb on the specified endpoint.
`500` | An unexpected error occurred.
<!--
## Paging & sorting
All `GET` endpoints returning a list of objects support pagination. The desired page of result is specified by providing the following HTTP query parameters:

Name | Description
------------------- | -----------
`page_number` | The page of data to retrieve
`page_size` | The number of items to display per page
`sort_by` | The field name to sort by
`sort_order` | The sort order (ASC or DESC)
-->