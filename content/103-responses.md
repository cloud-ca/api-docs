---
weight: 103
title: Responses
---

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

```shell
# Example without tasks
```

```output
{
  "data": [
    { "_comment" : "JSON representation of first object goes here" },
    { "_comment" : "JSON representation of second object goes here" }
  ]
}
```

```shell
# Example of compute API call with task
```

```output
{
  "taskId": "c2c13744-8610-4012-800a-0907bea110a5",
  "taskStatus": "PENDING"
}
```

When an API request is successful, the response body will contain the `data` field with the result of the API call. If you're using the [compute API](#compute-api), the `data` field might be empty since most of the operations are asynchronous. The response will contain the `taskId` and `taskStatus` fields so that you can retrieve the result of the operation you executed through the [task API](#tasks)

Attributes | Type | Description
---------- | ---- | -----------
`data` | Array[string] | The data field contains the object requested by the API caller
`taskId` | string | The [task id](#tasks) of an operation executed through the [compute API](#compute-api)
`taskStatus` | string | The status of a [task](#tasks) of an operation executed through the [compute API](#compute-api)
<!--
`metadata` | The metadata is an optionally returned field containing paging and sorting information
-->

<aside class="notice">
If the response contains the "errors" field, the request was <strong>not</strong> successful
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

Attributes | Description
---------- | -----------
`errors` | A list of errors objects that contain information about each error

Each error has additional fields to describe it :

Attributes | Description
---------- | -----------
`code` | The cloud.ca error code
`message` | A human readable explanation of the error code
`context` | Additional information

The HTTP status codes of error responses :

Status code | Reason
----------- | ------
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
---- | -----------
`page_number` | The page of data to retrieve
`page_size` | The number of items to display per page
`sort_by` | The field name to sort by
`sort_order` | The sort order (ASC or DESC)
-->
