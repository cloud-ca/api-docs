## Instances

### List instances

> The list instances response example:

```json
{
  "data": [
    {
      "zoneId": "04afdbd1-e32d-4999-86d0-96703736dded",
      "templateId": "8f52a74e-e637-40e8-a8dc-f56fd0b71ab9",
      "templateName": "CentOS 7 HVM base (64bit)",
      "computeOfferingId": "3caab5ed-b5a2-4d8a-82e4-51c46168ee6c",
      "zoneName": "QC-1",
      "computeOfferingName": "1vCPU.512MB",
      "networkId": "d5a68379-a9ee-404f-9492-a1964b374d6f",
      "networkName": "Web-Testing",
      "vpcId": "9eb1592c-f92f-4ddd-9799-b58caf896328",
      "vpcName": "Testing-VPC",
      "ipAddress": "10.164.212.68",
      "projectId": "a295c6de-1737-4df2-aa49-9bd749fa2489",
      "isPasswordEnabled": true,
      "macAddress": "02:00:2b:67:00:30",
      "cpuCount": 1,
      "memoryInMB": 512,
      "hostname": "backup-test",
      "username": "cca-user",
      "affinityGroupIds": [],
      "id": "9db8ff2f-b49b-466d-a2f3-c1e6def408f4",
      "name": "backup-test",
      "state": "Running"
    }
  ],
  "metadata": {
    "recordCount": 1
  }
}
```

```shell
curl -X GET "https://api.cloud.ca/v1/services/:service_code/:env_name/instances" -H "MC-Api-Key: [your-api-key]"
```

This endpoint retrieves all instances in a given environment.

`GET https://api.cloud.ca/v1/services/:service_code/:env_name/instances`

Instance

Fields | Description
------ | -----------
`id`<br>*UUID* | Instance ID
`name`<br>*string*, **required** | Instance's display name
`state>`<br>*string* | The current state of the instance.
`templateId`<br>*UUID*, **required** | Instance's template ID
`templateName`<br>*string* | Name of associated template
`computeOfferingId`<br>*UUID*, **required** | Instance's Compute Offering ID
`computeOfferingName`<br>*string* | Name of associated Compute Offering
`cpuCount`<br>*integer* | Number of vCPUs associated with the instance's Compute Offering.
`memoryInMB`<br>*integer* | Number of megabytes associated with the instance's Compute Offering.
`networkId`<br>*UUID*, **required** | ID of Network where instance is deployed
`networkName`<br>*string* | Name of associated Network
`hostName`<br>*string* | Instance's host name
`userName`<br>*string* | The username that can be used to connect to the instance
`affinityGroupIds`<br>*array* | ID(s) of the Affinity Groups to which the instance is associated.
`zoneId`<br>*UUID* | ID of zone where instance is deployed
`zoneName`<br>*string* | Name of associated Zone
`vpcId`<br>*UUID* | Instance's VPC ID
`vpcName`<br>*string* | Name of associated VPC
`ipAddress`<br>*string* | The instance's private IPv4 address
`projectId`<br>*UUID* | Instance's CloudStack project ID
`isPasswordEnabled`<br>*boolean* | Indicate whether a password can be used for remote connections
`macAddress`<br>*string* | The instance's MAC address

### Add new instance

> Here is the absolute minimum information required to create a new instance:

```shell
curl -X POST -H "Content-Type: application/json" -H "MC-Api-Key: [your-api-key]" -d "{
  \"name\" : \"myInstance2\",
  \"templateId\" : \"15601ee5-3db8-4021-9872-e5248a7f885a\",
  \"computeOfferingId\": \"e213fb17-ab2e-45ff-9679-e30f905f35a2\",
  \"networkId\" : \"d5a68379-a9ee-404f-9492-a1964b374d6f\"
}" "https://api.cloud.ca/v1/services/compute-east/testing/instances"
```
> The above command returns JSON structured like this:

```json
{
  "taskId": "b2f82e2a-123e-4f86-a4c7-dc9b850dd11e",
  "taskStatus": "PENDING"
}
```

> After querying the [Tasks](#tasks) endpoint with above `taskID`, a successful execution will return a result like this:

```json
{
   "data":{
      "id":"b2f82e2a-123e-4f86-a4c7-dc9b850dd11e",
      "status":"SUCCESS",
      "created":"2016-07-12T09:37:34.955-04:00",
      "result":{
         "cpuCount":1,
         "memoryInMB":1024,
         "affinityGroupIds":[],
         "networkId":"d5a68379-a9ee-404f-9492-a1964b374d6f",
         "state":"Running",
         "hostname":"myInstance",
         "isPasswordEnabled":true,
         "projectId":"a295c6de-1737-4df2-aa49-9bd749fa2489",
         "macAddress":"02:00:01:16:00:33",
         "type":"CloudStack",
         "password":"fJub6i",
         "zoneName":"QC-1",
         "zoneId":"04afdbd1-e32d-4999-86d0-96703736dded",
         "id":"5bf7352c-eed2-43dc-83f1-89917fb893ca",
         "templateId":"15601ee5-3db8-4021-9872-e5248a7f885a",
         "computeOfferingId":"e213fb17-ab2e-45ff-9679-e30f905f35a2",
         "computeOfferingName":"1vCPU.1GB",
         "name":"myInstance",
         "networkName":"Web-Testing",
         "templateName":"CentOS 7.2 HVM base (64bit)",
         "ipAddress":"10.164.212.242"
      }
   }
}
```

`POST https://api.cloud.ca/v1/services/:service_code/:env_name/instances`

Create a new instances in a given environment.
TODO


### Delete an instance

```shell
curl -X DELETE "https://api.cloud.ca/v1/services/compute-east/demo-env/instances/5bf7352c-eed2-43dc-83f1-89917fb893ca" \
  -H "MC-Api-Key: [your-api-key]"
```
> The above command returns JSON structured like this:

```json
{  
   "taskId":"07be5466-dd81-4965-929e-e72cfa35046f",
   "taskStatus":"PENDING"
}
```

> Schema for `cleanup_options` parameter:

```json
{
   "purgeImmediately":true,
   "publicIpIdsToRelease":[
      "string"
   ],
   "volumeIdsToDelete":[
      "string"
   ],
   "deleteSnapshots":true
}
```
`DELETE https://api.cloud.ca/v1/services/:service_code/:env_name/instances/:instance_id`

This endpoint deletes an instance. The instance needs to be in running, stopped or error state for the operation to work.

#### Parameters

Parameter | Type | Required | Description
--------- | ---- | ------- | -----------
service_code | path | true | Service code of an environment.
env_name | path | true | Environment name.
id | path | true | Id of instance.
org_id | query | false | Organization id (not required if environment is in your own organization).
cleanup_options | body | false | JSON-formatted cleanup options
