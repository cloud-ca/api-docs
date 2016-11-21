### VPCs

A Virtual Private Cloud (VPC) is a logically isolated section of cloud.ca, where you can build a multi-tier application architecture.

<!-------------------- LIST VPCS -------------------->


#### List VPCs

```shell
curl -X GET -H "MC-Api-Key: [your-api-key]"
"https://api.cloud.ca/v1/services/compute-qc/prod/vpcs"

# Example:
```
```json
{
  "data": [{
    "id": "9fe8e398-06d6-482c-8f55-b805bde4d3cc",
    "name": "MyVPC",
    "description": "Some VPC",
    "cidr": "10.155.24.0/22",
    "zoneId": "04afdbd1-e32d-4999-86d0-96703736dded",
    "zoneName": "QC-1",
    "state": "Enabled",
    "networkDomain": "hello.world",
    "vpcOfferingId": "21a40b85-5fa9-440f-ab77-5e560073b584",
    "requiresUpgrade": false,
    "sourceNatIp": "172.31.3.253",
    "vpnStatus": "Disabled"
  }],
  "metadata": {
    "recordCount": 1
  }
}
```

<code>GET https://api.cloud.ca/v1/services/<a href="#service-connections">:service_code</a>/<a href="#environments">:environment_name</a>/vpcs</code>

Retrieve a list of all VPCs of an environment.

Attributes | &nbsp;
---------- | -----
`id`<br/>*UUID* | The id of the VPC
`name`<br/>*string* | The name of the VPC
`description`<br/>*string* | The description of the VPC
`cidr`<br/>*string* | The CIDR of a VPC
`zoneId`<br/>*string* | The id of the zone where the VPC was created
`zoneName`<br/>*string* | The name of the zone where the VPC was created
`state`<br/>*string* | The state of the VPC
`networkDomain`<br/>*string* | A custom DNS suffix at the level of a network
`requiresUpgrade`<br/>*string* | true if the VPC needs to be upgraded
`sourceNatIp`<br/>*string* | The source NAT IP of the VPC
`vpnStatus`<br/>*string* | The status of the [VPN](#vpn). The status can be `ENABLED` or `DISABLED`


<!-------------------- RETRIEVE A VPC -------------------->


#### Retrieve a VPC

```shell
curl -X GET -H "MC-Api-Key: [your-api-key]"
"https://api.cloud.ca/v1/services/compute-qc/prod/vpcs/ad5bcae8-ee8b-4ee8-a7a4-381c25444b8e"

# Example:
```
```json
{
  "data": {
    "id": "9fe8e398-06d6-482c-8f55-b805bde4d3cc",
    "name": "MyVPC",
    "description": "Some VPC",
    "cidr": "10.155.24.0/22",
    "zoneId": "04afdbd1-e32d-4999-86d0-96703736dded",
    "zoneName": "QC-1",
    "state": "Enabled",
    "networkDomain": "hello.world",
    "vpcOfferingId": "21a40b85-5fa9-440f-ab77-5e560073b584",
    "requiresUpgrade": false,
    "sourceNatIp": "172.31.3.253",
    "vpnStatus": "Disabled"
  }
}
```

<code>GET https://api.cloud.ca/v1/services/<a href="#service-connections">:service_code</a>/<a href="#environments">:environment_name</a>/vpcs/:id</code>

Retrieve information about a VPC.

Attributes | &nbsp;
---------- | -----
`id`<br/>*UUID* | The id of the VPC
`name`<br/>*string* | The name of the VPC
`description`<br/>*string* | The description of the VPC
`cidr`<br/>*string* | The CIDR of a VPC
`zoneId`<br/>*string* | The id of the zone where the VPC was created
`zoneName`<br/>*string* | The name of the zone where the VPC was created
`state`<br/>*string* | The state of the VPC
`networkDomain`<br/>*string* | A custom DNS suffix at the level of a network
`requiresUpgrade`<br/>*string* | true if the VPC needs to be upgraded
`sourceNatIp`<br/>*string* | The source NAT IP of the VPC
`vpnStatus`<br/>*string* | The status of the [VPN](#vpn). The status can be `ENABLED` or `DISABLED`


<!-------------------- CREATE A VPC -------------------->


#### Create a VPC


```shell

# Example:

curl -X POST -H "Content-Type: application/json" -H "MC-Api-Key: [your-api-key]" -d "{
  \"name\" : \"ultron\",
  \"templateId\" : \"15601ee5-3db8-4021-9872-e5248a7f885a\",
  \"computeOfferingId\": \"e213fb17-ab2e-45ff-9679-e30f905f35a2\",
  \"networkId\" : \"d5a68379-a9ee-404f-9492-a1964b374d6f\"
}" "https://api.cloud.ca/v1/services/compute-qc/prod/vpcs"

# Request example:
```
```json
{
  "name": "my_vpc",
  "description": "My prod VPC",
  "vpcOfferingId": "21a40b85-5fa9-440f-ab77-5e560073b584",
  "networkDomain": "hello.world"
}
```
```go
resources, _ := ccaClient.GetResources("compute-qc", "prod")
ccaResources := resources.(cloudca.Resources)
createdVpc, err := ccaResources.Vpcs.Create(cloudca.Instance{
        Name: "my_vpc",
        Description: "My prod VPC",
        VpcOfferingId: "21a40b85-5fa9-440f-ab77-5e560073b584",
        NetworkDomain:"hello.world"
    })
```
```dart
resource "cloudca_vpc" "my_vpc" {
    service_code = "compute-qc"
    environment_name = "prod"
    name = "my_vpc"
    description = "This is a test vpc"
    vpc_offering = "Default VPC offering"
}
```

<code>POST https://api.cloud.ca/v1/services/<a href="#service-connections">:service_code</a>/<a href="#environments">:environment_name</a>/vpcs</code>

Create a VPC in an environment.

Required | &nbsp;
------ | ---- | -----------
`name`<br/>*string* | The name of the new VPC
`description`<br/>*string* | The description of the new VPC
`vpcOfferingId`<br/>*UUID* | The id of the VPC offering to use for the new VPC

Optional | &nbsp;
------ | ---- | -----------
`networkDomain`<br/>*string* | A custom DNS suffix at the level of a network


<!-------------------- UPDATE A VPC -------------------->


#### Update a VPC


```shell

# Example:

curl -X PUT -H "Content-Type: application/json" -H "MC-Api-Key: [your-api-key]" -d "{
  \"name\": \"my_updated_vpc\",
  \"description\": \"My prod VPC\"
}" "https://api.cloud.ca/v1/services/compute-qc/prod/vpcs/d77e1ab1-0320-4504-83c5-e78b431c7577"

# Request example:
```
```json
{
  "name": "my_updated_vpc",
  "description": "My prod VPC"
}
```
```go
resources, _ := ccaClient.GetResources("compute-qc", "prod")
ccaResources := resources.(cloudca.Resources)
updatedVpc, err := ccaResources.Vpcs.Update(cloudca.Vpc{
        Id: "d77e1ab1-0320-4504-83c5-e78b431c7577",
        Name: "my_updated_vpc",
        Description: "My prod VPC",
    })
```

<code>POST https://api.cloud.ca/v1/services/<a href="#service-connections">:service_code</a>/<a href="#environments">:environment_name</a>/vpcs</code>

Create a VPC in your environment.

Optional | &nbsp;
------ | ---- | -----------
`name`<br/>*string* | The new name of the VPC
`description`<br/>*string* | The new description of the VPC


<!-------------------- DELETE A VPC -------------------->


#### Destroy a VPC


```shell

# Example:

curl -X DELETE -H "MC-Api-Key: [your-api-key]"
"https://api.cloud.ca/v1/services/compute-qc/prod/vpcs/ad5bcae8-ee8b-4ee8-a7a4-381c25444b8e"
```
```go
resources, _ := ccaClient.GetResources("compute-qc", "prod")
ccaResources := resources.(cloudca.Resources)
success, err := ccaResources.Vpcs.Destroy("ad5bcae8-ee8b-4ee8-a7a4-381c25444b8e")
```

<code>DELETE https://api.cloud.ca/v1/services/<a href="#service-connections">:service_code</a>/<a href="#environments">:environment_name</a>/vpcs/:id</code>

Destroy an existing VPC.

<!-------------------- RESTART A VPC -------------------->


#### Restart a VPC


```shell

# Example:

curl -X POST -H "Content-Type: application/json" -H "MC-Api-Key: [your-api-key]"
"https://api.cloud.ca/v1/services/compute-qc/prod/vpcs/ad5bcae8-ee8b-4ee8-a7a4-381c25444b8e?operation=restart"
```
```go
resources, _ := ccaClient.GetResources("compute-qc", "prod")
ccaResources := resources.(cloudca.Resources)
success, err := ccaResources.Vpcs.RestartRouter("ad5bcae8-ee8b-4ee8-a7a4-381c25444b8e")
```

<code>POST https://api.cloud.ca/v1/services/<a href="#service-connections">:service_code</a>/<a href="#environments">:environment_name</a>/vpcs/:id?operation=restart</code>

Restart the router of a VPC.
