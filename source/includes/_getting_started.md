# Getting Started

## Welcome to cloud.ca's API documentation.

The cloud.ca API allows you to manage your configuration as well as provision and manage your resources in a simple programmatic way using standard HTTP requests.

The API is  [RESTful](https://en.wikipedia.org/wiki/Representational_state_transfer). All requests should be made over SSL. Request and Response bodies, including errors, are encoded in JSON.

## Authentication
<!--
```shell
## To authenticate, add a header
## Make sure to replace `[your-api-key]` with your API key.
curl "https://api.cloud.ca/v1" -H "MC-Api-Key: [your-api-key]"
```

```javascript
//GET https://api.cloud.ca/v1 with header MC-Api-Key:[your-api-key]
// Response :
{
   status : "ACTIVE"
}
```
-->
Authentication is done via the API Key which you can find in the API Keys section in the cloud.ca portal under the user profile menu. If you don't see cloud.ca API section, it means your user account doesn't have the required **API keys for cloud.ca** permission.

cloud.ca expects for the API key to be included in all API requests to the server in a header that looks like the following:

`MC-Api-Key: [your-api-key]`

<aside class="notice">
You must replace <code>"[your-api-key]</code> with your personal cloud.ca API key.
</aside>

## HTTP verbs
The cloud.ca API can be used by any tool that is fluent in HTTP. The appropriate HTTP method should be used depending on the desired action.

Method | Purpose
------ | -------
GET | Used to retrieve information about a resource.
POST | Used to create (or provision) a new resource or perform an operation on it.
PUT | Used to update a resource.
DELETE | Used to remove/delete a resource.

POST and PUT requests must have a JSON encoded body and the `Content-Type: application/json` header.

<aside class="notice">
Remember to url-encode all querystring parameters
</aside>

## Paging & sorting
All `GET` endpoints returning a list of objects support pagination. The desired page of result is specified by providing the following HTTP query parameters:

Name | Description
------------------- | -----------
page_number | The page of data to retrieve
page_size | The number of items to display per page
sort_by | The field name to sort by
sort_order | The sort order (ASC or DESC)

## Response structures

### Success
> A successful request to return a single resource will look like this:

```json
{
  "data": {
    "_comment" : " JSON representation of resource goes here"
  }
}
```

> A successful request to return a collection of resource will look like this:

```json
{
  "data": [
    { "_comment" : "JSON representation of first resource goes here" },
    { "_comment" : "JSON representation of second resource goes here" }
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

When an API request is issued, the response body will be formatted in the same standard JSON structure, although some of the object and attributes may or may not be included depending on the context.

### Error
> An unsuccessful request will look like this:

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
The returned HTTP Status will be one of the following codes:

Status code | Reason
----------- | -------
200 | The request was successful.
400 | Bad request -- Occurs when invalid parameters are provided or when quota limit is exceeded.
403 | Forbidden -- Not authorized to perform this request.
404 | Not Found -- Cannot locate the specified endpoint.
405 | Method not allowed -- Cannot use that HTTP verb on the specified endpoint.
500 | An unexpected error occurred.

## Service API endpoints
### Standard endpoint
Cloud.ca provides its own native API for the services that it provides. It enforces the same environment role-based access control that is defined in the cloud.ca portal.

The service API has the same starting point for every service:

`https://api.cloud.ca/v1/services/:service_code/:env_name/:entity_type`

Service code | Description | Zones
--- | --- | ---
compute-on | Service code for the Ontario region | ON-1
compute-qc | Service code for the Quebec region | QC-1, QC-2

All compute service API calls must include path parameters `service_code` and `env_name`, which are used to specify which environment is targeted by your request. This information can be retrieved from the **Environment** picker in the **Services** tab.


### Service Operations

Some operations take longer to execute, and to avoid blocking on the response until it is fully completed, these are treated in an asynchronous fashion. This means the API will return immediately, and provide you a `taskId` that is your reference to the ongoing background task. Using the [Tasks](#tasks) API, you can query the task's status to find if it has completed and obtain the result of the operation.

<aside class="notice">
It is a good practice to limit the polling rate on the task API to no more than once per second.
</aside>
