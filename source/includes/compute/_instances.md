## Instances

### Instance resource
```shell
# Example of instance response
```
```json
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
```

Generic instance information

Attributes | &nbsp;
------ | ---- | -----------
`id`<br/>*UUID* | Instance ID
`name`<br/>*string* | Instance's display name
`state`<br/>*string* | The current state of the instance.
`templateId`<br/>*UUID* | Instance's template ID
`templateName`<br/>*string* | Name of associated template
`computeOfferingId`<br/>*UUID* | Instance's Compute Offering ID
`computeOfferingName`<br/>*string* | Name of associated Compute Offering
`cpuCount`<br/>*integer* | Number of vCPUs associated with the instance's Compute Offering.
`memoryInMB`<br/>*integer* | Number of megabytes associated with the instance's Compute Offering.
`networkId`<br/>*UUID* | ID of Network where instance is deployed
`networkName`<br/>*string* | Name of associated Network
`hostName`<br/>*string* | Instance's host name
`userName`<br/>*string* | The username that can be used to connect to the instance
`affinityGroupIds`<br/>*Array[UUID]* | ID(s) of the Affinity Groups to which the instance is associated.
`zoneId`<br/>*UUID* | ID of zone where instance is deployed
`zoneName`<br/>*string* | Name of associated Zone
`vpcId`<br/>*UUID* | Instance's VPC ID
`vpcName`<br/>*string* | Name of associated VPC
`ipAddress`<br/>*string* | The instance's private IPv4 address
`projectId`<br/>*UUID* | Instance's CloudStack project ID
`isPasswordEnabled`<br/>*boolean* | Indicate whether a password can be used for remote connections
`macAddress`<br/>*string* | The instance's MAC address


### List instances

```shell
curl -X GET "https://api.cloud.ca/v1/services/compute-qc/demo-env/instances"
  -H "MC-Api-Key: [your-api-key]"

# The above command returns JSON structured like this:

```
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

<code>GET https://api.cloud.ca/v1/services/<a href="#service-connections">:service_code</a>/<a href="#environments">:environment_name</a>/instances</code>

This endpoint retrieves all instances in a given environment.

### Create an instance

```shell

# Here is the absolute minimum information required to create a new instance:

curl -X POST -H "Content-Type: application/json" -H "MC-Api-Key: [your-api-key]" -d "{
  \"name\" : \"myInstance2\",
  \"templateId\" : \"15601ee5-3db8-4021-9872-e5248a7f885a\",
  \"computeOfferingId\": \"e213fb17-ab2e-45ff-9679-e30f905f35a2\",
  \"networkId\" : \"d5a68379-a9ee-404f-9492-a1964b374d6f\"
}" "https://api.cloud.ca/v1/services/compute-qc/testing/instances"

# After querying the [Tasks](#tasks) endpoint with above `taskID`, a successful execution will return a result like this:

```
```json
{
   "data":{
      "id":"b2f82e2a-123e-4f86-a4c7-dc9b850dd11e",
      "status":"SUCCESS",
      "created":"2016-07-12T09:37:34.955-04:00",
      "result":{
         "cpuCount":1,
         "memoryInMB":1024,
         "affinityGroupIds":[

         ],
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
 <code>POST https://api.cloud.ca/v1/services/<a href="#service-connections">:service_code</a>/<a href="#environments">:environment_name</a>/instances</code>

This endpoint create a new instances in a given environment.

Required | &nbsp;
------ | ---- | -----------
`name`<br/>*string* | Name of the newly created instance
`templateId`<br/>*UUID* | The template to use for this instance
`computeOfferingId`<br/>*UUID* | The [compute offering](#compute-offerings) will determine the number of CPU and RAM of your instance
`networkId`<br/>*UUID* | The [tier](#tiers) in which the instance will be created. If you don't have a tier, it can be created through the [create tier](#create-tier) api.

Optional | &nbsp;
------ | ---- | -----------
`diskOfferingId`<br/>*UUID* | The [disk offering](#disk-offerings) to be used for a new volume to attach to this instance
`additionalDiskSizeInGb`<br/>*UUID* | The number of GB the additional disk should have. You must choose a disk offering with custom disk size enabled.
`additionalDiskIops`<br/>*UUID* | The number of IOPS the additional disk should have. You must choose a disk offering with custom IOPS enabled.
`sshKeyName`<br/>*string* | The name of the [SSH key](#ssh-keys) to use for this instance. If you don't have an SSH key registered, you can do so through this [api](#create-ssh-key).
`publicKey`<br/>*string* | The public key to use for this instance.
`volumeIdToAttach`<br/>*UUID* | The [volume](#volumes) to attach to this instance.
`affinityGroupId`<br/>*UUID* | The [affinity group](#affinity-groups) where to create the instance.
`portsToForward`<br/>*array[string]* | The ports...
`userData`<br/>*string* | User data...



### Delete an instance

```shell
curl -X DELETE "https://api.cloud.ca:443/v1/services/compute-east/demo-env/instances/5bf7352c-eed2-43dc-83f1-89917fb893ca" \
  -H "MC-Api-Key: [your-api-key]"

# Schema for `cleanup_options` parameter:

```
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
<code>DELETE https://api.cloud.ca/v1/services/<a href="#service-connections">:service_code</a>/<a href="#environments">:environment_name</a>/instances/:id</code>

This endpoint deletes an instance. The instance needs to be in running, stopped or error state for the operation to work.
