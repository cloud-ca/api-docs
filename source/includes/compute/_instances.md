### Instances

<!-------------------- GENERAL INSTANCE INFORMATION -------------------->

#### Instance resource
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

<!-------------------- LIST INSTANCES -------------------->

#### List instances

```shell
curl -X GET -H "MC-Api-Key: [your-api-key]"
"https://api.cloud.ca/v1/services/compute-qc/demo-env/instances"

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

<!-------------------- RETRIEVE AN INSTANCE -------------------->

#### Retrieve an instance

```shell
curl -X GET -H "MC-Api-Key: [your-api-key]"
"https://api.cloud.ca/v1/services/compute-qc/demo-env/instances/5951c2b8-e901-4c01-8ae0-cb8d7c508d29"


# The above command returns JSON structured like this:

```
```json
{
  "data": {
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
}
```

<code>GET https://api.cloud.ca/v1/services/<a href="#service-connections">:service_code</a>/<a href="#environments">:environment_name</a>/instances/:id</code>

This endpoint retrieves a specific instance.


<!-------------------- CREATE AN INSTANCE -------------------->

#### Create an instance

```shell

# Here is the absolute minimum information required to create a new instance:

curl -X POST -H "Content-Type: application/json" -H "MC-Api-Key: [your-api-key]" -d "{
  \"name\" : \"ultron\",
  \"templateId\" : \"15601ee5-3db8-4021-9872-e5248a7f885a\",
  \"computeOfferingId\": \"e213fb17-ab2e-45ff-9679-e30f905f35a2\",
  \"networkId\" : \"d5a68379-a9ee-404f-9492-a1964b374d6f\"
}" "https://api.cloud.ca/v1/services/compute-qc/testing/instances"

# Request should look like this

```
```json
{
   "name": "jarvis",
   "templateId": "",
   "computeOfferingId": "",
   "networkId": "",
   "diskOfferingId": "",
   "additionalDiskSizeInGb": 20,
   "additionalDiskIops": 1000,
   "sshKeyName": "mysshkey",
   "volumeIdToAttach": "",
   "affinityGroupId": "",
   "portsToForward": ["80", "9999"],
   "userData": "#!/bin/bash\necho 'hello world'"
}
```
 <code>POST https://api.cloud.ca/v1/services/<a href="#service-connections">:service_code</a>/<a href="#environments">:environment_name</a>/instances</code>

This endpoint create a new instances in a given environment.

Required | &nbsp;
------ | ---- | -----------
`name`<br/>*string* | Name of the newly created instance
`templateId`<br/>*UUID* | The [template](#templates) to use for this instance
`computeOfferingId`<br/>*UUID* | The [compute offering](#compute-offerings) will determine the number of CPU and RAM of your instance
`networkId`<br/>*UUID* | The [tier](#tiers) in which the instance will be created. If you don't have a tier, it can be created through the [create tier](#create-tier) api.

Optional | &nbsp;
------ | ---- | -----------
`diskOfferingId`<br/>*UUID* | The [disk offering](#disk-offerings) to be used for a new volume to attach to this instance
`additionalDiskSizeInGb`<br/>*int* | The number of GB the additional disk should have. You must choose a disk offering with custom disk size enabled.
`additionalDiskIops`<br/>*int* | The number of IOPS the additional disk should have. You must choose a disk offering with custom IOPS enabled.
`sshKeyName`<br/>*string* | The name of the [SSH key](#ssh-keys) to use for this instance. If you don't have an SSH key registered, you can do so through this [api](#create-ssh-key).
`publicKey`<br/>*string* | The public key to use for this instance.
`volumeIdToAttach`<br/>*UUID* | The [volume](#volumes) to attach to this instance.
`affinityGroupId`<br/>*UUID* | The [affinity group](#affinity-groups) where to create the instance.
`portsToForward`<br/>*array[string]* | The [ports](#port-forwarding-rules) you would like to open on the instance. It will try to use an existing [public IP address](#public-ips), if it can't find one it will [acquire a new public IP](#acquire-a-public-ip).
`userData`<br/>*string* | User data is data that can be accessed and interpreted in the instance. You can read about common use cases [here](https://cloudops.cloud.ca/kb/en/compute-service#working-with-instances).


<!-------------------- UPDATE AN INSTANCE -------------------->


#### Update an instance


```shell

# Here is the absolute minimum information required to create a new instance:

curl -X PUT -H "Content-Type: application/json" -H "MC-Api-Key: [your-api-key]" -d "{
  \"name\" : \"e_c137\",
  \"hostname\" : \"e_c137\",
}" "https://api.cloud.ca/v1/services/compute-qc/testing/instances/5951c2b8-e901-4c01-8ae0-cb8d7c508d29"

# Request example:
```
```json
{
   "name": "hal",
   "hostname": "hal_9000"
}
```
 <code>POST https://api.cloud.ca/v1/services/<a href="#service-connections">:service_code</a>/<a href="#environments">:environment_name</a>/instances/:id</code>

This endpoint updates an existing instance.

Optional | &nbsp;
------ | ---- | -----------
`name`<br/>*string* | Updated name of instance
`hostname`<br/>*string* | Updated hostname of instance.


<!-------------------- DELETE AN INSTANCE -------------------->

#### Delete an instance

```shell
curl -X DELETE -H "Content-Type: application/json" -H "MC-Api-Key: [your-api-key]"
"https://api.cloud.ca:443/v1/services/compute-east/demo-env/instances/5bf7352c-eed2-43dc-83f1-89917fb893ca" \


# Request example:

```
```json
{
   "purgeImmediately":true,
   "deleteSnapshots":true,
   "publicIpIdsToRelease":[
      "fe446d61-a22c-403a-87bf-5351e65dc54d"
   ],
   "volumeIdsToDelete":[
      "e3d4045d-3ef7-464d-92a3-fc18269f36e2
"
   ],
}
```
<code>DELETE https://api.cloud.ca/v1/services/<a href="#service-connections">:service_code</a>/<a href="#environments">:environment_name</a>/instances/:id</code>

This endpoint deletes an instance. The instance needs to be in running, stopped or error state for the operation to work.


Optional | &nbsp;
------ | ---- | -----------
`purgeImmediately`<br/>*boolean* | Will destroy and purge the instance if true, puts the instance in destroyed state otherwise. An instance that wasn't purged can be recovered.
`deleteSnapshots`<br/>*boolean* | Will delete all [snapshots](#snapshots) of volumes attached to this instance if true, will keep snapshots otherwise.
`publicIpIdsToRelease`<br/>*Array[UUID]* | List of IDs of the [public IP addresses](#public-ips) to release with the instance. Can only release public IPs of the instance being destroyed and they must not be used by other instances.
`volumeIdsToDelete`<br/>*Array[UUID]* | List of IDs of the [data volumes](#volumes) to delete with the instance. Can only destroy data volumes that are attached to this instance.

<!-------------------- START AN INSTANCE -------------------->


#### Start an instance


```shell

# Example:

curl -X POST -H "Content-Type: application/json" -H "MC-Api-Key: [your-api-key]"
"https://api.cloud.ca/v1/services/compute-qc/testing/instances/5951c2b8-e901-4c01-8ae0-cb8d7c508d29?operation=start"

```

 <code>POST https://api.cloud.ca/v1/services/<a href="#service-connections">:service_code</a>/<a href="#environments">:environment_name</a>/instances/:id?operation=start</code>

This endpoint starts an existing instance.


<!-------------------- STOP AN INSTANCE -------------------->


#### Stop an instance


```shell

# Example:

curl -X POST -H "Content-Type: application/json" -H "MC-Api-Key: [your-api-key]"
"https://api.cloud.ca/v1/services/compute-qc/testing/instances/5951c2b8-e901-4c01-8ae0-cb8d7c508d29?operation=stop"

```

 <code>POST https://api.cloud.ca/v1/services/<a href="#service-connections">:service_code</a>/<a href="#environments">:environment_name</a>/instances/:id?operation=stop</code>

This endpoint stops an existing instance.

<!-------------------- REBOOT AN INSTANCE -------------------->


#### Reboot an instance


```shell

# Example:

curl -X POST -H "Content-Type: application/json" -H "MC-Api-Key: [your-api-key]"
"https://api.cloud.ca/v1/services/compute-qc/testing/instances/5951c2b8-e901-4c01-8ae0-cb8d7c508d29?operation=reboot"

```

 <code>POST https://api.cloud.ca/v1/services/<a href="#service-connections">:service_code</a>/<a href="#environments">:environment_name</a>/instances/:id?operation=reboot</code>

This endpoint reboots an existing instance.


<!-------------------- PURGE AN INSTANCE -------------------->


#### Purge an instance


```shell

# Example:

curl -X POST -H "Content-Type: application/json" -H "MC-Api-Key: [your-api-key]"
"https://api.cloud.ca/v1/services/compute-qc/testing/instances/5951c2b8-e901-4c01-8ae0-cb8d7c508d29?operation=purge"

```

 <code>POST https://api.cloud.ca/v1/services/<a href="#service-connections">:service_code</a>/<a href="#environments">:environment_name</a>/instances/:id?operation=purge</code>

This endpoint purges an existing instance.


<!-------------------- RECOVER AN INSTANCE -------------------->


#### Recover an instance


```shell

# Example:

curl -X POST -H "Content-Type: application/json" -H "MC-Api-Key: [your-api-key]"
"https://api.cloud.ca/v1/services/compute-qc/testing/instances/5951c2b8-e901-4c01-8ae0-cb8d7c508d29?operation=recover"

```

 <code>POST https://api.cloud.ca/v1/services/<a href="#service-connections">:service_code</a>/<a href="#environments">:environment_name</a>/instances/:id?operation=purge</code>

This endpoint purges an existing instance.


<!-------------------- CHANGE COMPUTE OFFERING OF AN INSTANCE -------------------->


#### Change the compute offering of an instance


```shell

# Example:

curl -X POST -H "Content-Type: application/json" -H "MC-Api-Key: [your-api-key]"
"https://api.cloud.ca/v1/services/compute-qc/testing/instances/5951c2b8-e901-4c01-8ae0-cb8d7c508d29?operation=changeComputeOffering"

```

 <code>POST https://api.cloud.ca/v1/services/<a href="#service-connections">:service_code</a>/<a href="#environments">:environment_name</a>/instances/:id?operation=changeComputeOffering</code>

This endpoint changes the compute offering an existing instance.


<!-------------------- CHANGE COMPUTE OFFERING OF AN INSTANCE -------------------->


#### Reset the password of an instance


```shell

# Example:

curl -X POST -H "Content-Type: application/json" -H "MC-Api-Key: [your-api-key]"
"https://api.cloud.ca/v1/services/compute-qc/testing/instances/5951c2b8-e901-4c01-8ae0-cb8d7c508d29?operation=resetPassword"

```

 <code>POST https://api.cloud.ca/v1/services/<a href="#service-connections">:service_code</a>/<a href="#environments">:environment_name</a>/instances/:id?operation=resetPassword</code>

This endpoint resets the password of an existing instance.


<!-------------------- ASSOCIATE AN SSH KEY TO AN INSTANCE -------------------->


#### Associate an SSH key to an instance


```shell

# Example:

curl -X POST -H "Content-Type: application/json" -H "MC-Api-Key: [your-api-key]"
"https://api.cloud.ca/v1/services/compute-qc/testing/instances/5951c2b8-e901-4c01-8ae0-cb8d7c508d29?operation=associateSSHKey"

```

 <code>POST https://api.cloud.ca/v1/services/<a href="#service-connections">:service_code</a>/<a href="#environments">:environment_name</a>/instances/:id?operation=associateSSHKey</code>

This endpoint associates an SSH key to an existing instance.
