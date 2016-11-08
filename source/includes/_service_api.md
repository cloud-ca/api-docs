# Service API
## Standard endpoint
Although CloudStack provides its own  native API, you may find it more convenient to use cloud.ca's wrapper for it, as it arguably simpler to use and provide a consistent way of calling all its supported services. Furthermore, it enforces the same environment role-based access control that is defined in the cloud.ca portal.

All compute service API calls must include path parameters `service_code` and `env_name`, which are used to specify which environment is targeted by your request. This information can be retrieved from the **Environment** picker in the **Services** tab, as seen below.

![Retrieve service_code and env_name](/images/service_environment.png)


## Asynchronous operations

Some operations take longer to execute, and to avoid blocking on the response until it is fully completed, these are treated in an asynchronous fashion. This means the API will return immediately, and provide you a `taskId` that is your reference to the ongoing background task. Using the [Tasks](#tasks) API, you can query the task's status to find if it has completed and obtain the result of the operation.

The operations that are affected by this are identified as such with a ***(async)*** suffix in this documentation.

<aside class="warning">
It is a good practice to limit the polling rate on the task API to no more than once per second.
</aside>
