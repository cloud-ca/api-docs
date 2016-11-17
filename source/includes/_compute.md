# Compute API

Cloud.ca provides its own native API for the services that it provides. It enforces the same environment role-based access control that is defined in the cloud.ca portal.

The service API has the same starting point for every service:

<code>https://api.cloud.ca/v1/services/<a href="#service-connections">:service_code</a>/<a href="#environments">:environment_name</a>/:entity_type</code>

Service code | Description | Zones
--- | --- | ---
compute-on | Service code for the Ontario region | ON-1
compute-qc | Service code for the Quebec region | QC-1, QC-2

All compute service API calls must include path parameters `service_code` and `env_name`, which are used to specify which environment is targeted by your request. This information can be retrieved from the **Environment** picker in the **Services** tab.

Some operations take longer to execute, and to avoid blocking on the response until it is fully completed, these are treated in an asynchronous fashion. This means the API will return immediately, and provide you a `taskId` that is your reference to the ongoing background task. Using the [Tasks](#tasks) API, you can query the task's status to find if it has completed and obtain the result of the operation.

<aside class="notice">
It is a good practice to limit the polling rate on the task API to no more than once per second.
</aside>

```shell
# The above command returns JSON structured like this:
```
```json
{
  "taskId": "b2f82e2a-123e-4f86-a4c7-dc9b850dd11e",
  "taskStatus": "PENDING"
}
```