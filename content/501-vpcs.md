---
weight: 501
title: VPCs
---

## VPCs

A Virtual Private Cloud (VPC) is a logically isolated section of cloud.ca, where you can build a multi-network application architecture.

### List VPCs

```shell
curl -X GET \
   -H "MC-Api-Key: your_api_key" \
   "https://api.cloud.ca/v1/services/compute-on/test_area/vpcs"

# Example response:
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
```go
resources, _ := ccaClient.GetResources("compute-on", "test_area")
ccaResources := resources.(cloudca.Resources)
vpcs, err := ccaResources.Vpcs.List()
```

<span class="method">GET</span> <code>/services/<a href="#service-connections">:service_code</a>/<a href="#environments">:environment_name</a>/vpcs</code>

Retrieve a list of all VPCs of an [environment](#environments)

Attributes | Type | Description
---------- | ---- | ------------
`id` | *UUID* | The id of the VPC
`name` | *string* | The name of the VPC
`description` | *string* | The description of the VPC
`cidr` | *string* | The CIDR of a VPC
`zoneId` | *string* | The id of the [zone](#zones) where the VPC was created
`zoneName` | *string* | The name of the [zone](#zones) where the VPC was created
`state` | *string* | The state of the VPC
`networkDomain` | *string* | A custom DNS suffix at the level of a network
`requiresUpgrade` | *string* | true if the VPC needs to be upgraded
`sourceNatIp` | *string* | The source NAT IP of the VPC
`vpnStatus` | *string* | The status of the [VPN](#vpn). The status can be `ENABLED` or `DISABLED`


<!-------------------- RETRIEVE A VPC -------------------->


### Retrieve a VPC

```shell
curl -X GET \
   -H "MC-Api-Key: your_api_key" \
   "https://api.cloud.ca/v1/services/compute-on/test_area/vpcs/ad5bcae8-ee8b-4ee8-a7a4-381c25444b8e"

# Example response:
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
```go
resources, _ := ccaClient.GetResources("compute-on", "test_area")
ccaResources := resources.(cloudca.Resources)
vpc, err := ccaResources.Vpcs.Get("ad5bcae8-ee8b-4ee8-a7a4-381c25444b8e")
```

<span class="method">GET</span> <code>/services/<a href="#service-connections">:service_code</a>/<a href="#environments">:environment_name</a>/vpcs/:id</code>

Retrieve information about a VPC.

Attributes | Type | Description
---------- | ---- | ------------
`id` | *UUID* | The id of the VPC
`name` | *string* | The name of the VPC
`description` | *string* | The description of the VPC
`cidr` | *string* | The CIDR of a VPC
`zoneId` | *string* | The id of the [zone](#zones) where the VPC was created
`zoneName` | *string* | The name of the [zone](#zones) where the VPC was created
`state` | *string* | The state of the VPC
`networkDomain` | *string* | A custom DNS suffix at the level of a network
`requiresUpgrade` | *string* | true if the VPC needs to be upgraded
`sourceNatIp` | *string* | The source NAT IP of the VPC
`vpnStatus` | *string* | The status of the [VPN](#vpn). The status can be `ENABLED` or `DISABLED`


<!-------------------- CREATE A VPC -------------------->


### Create a VPC


```shell

# Example:

curl -X POST \
   -H "Content-Type: application/json" \
   -H "MC-Api-Key: your_api_key" \
   -d "request_body" \
   "https://api.cloud.ca/v1/services/compute-on/test_area/vpcs"

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
resources, _ := ccaClient.GetResources("compute-on", "test_area")
ccaResources := resources.(cloudca.Resources)
createdVpc, err := ccaResources.Vpcs.Create(cloudca.Vpc{
        Name: "my_vpc",
        Description: "My prod VPC",
        VpcOfferingId: "21a40b85-5fa9-440f-ab77-5e560073b584",
        NetworkDomain:"hello.world"
    })
```
```dart
resource "cloudca_vpc" "my_vpc" {
    service_code = "compute-on"
    environment_name = "test_area"
    name = "my_vpc"
    description = "This is a test vpc"
    vpc_offering = "Default VPC offering"
}
```

<span class="method">POST</span> <code>/services/<a href="#service-connections">:service_code</a>/<a href="#environments">:environment_name</a>/vpcs</code>

Create a VPC in an [environment](#environments)

Required | Type | Description
-------- | ---- | -----------
`name` | *string* | The name of the new VPC
`description` | *string* | The description of the new VPC
`vpcOfferingId` | *UUID* | The id of the [VPC offering](#vpc-offerings) to use for the new VPC

Optional | Type | Description
------------ | ---- | -----------
`networkDomain` | *string* | A custom DNS suffix at the level of a network


<!-------------------- UPDATE A VPC -------------------->


### Update a VPC


```shell

# Example:

curl -X PUT \
   -H "Content-Type: application/json" \
   -H "MC-Api-Key: your_api_key" \
   -d "request_body" \
   "https://api.cloud.ca/v1/services/compute-on/test_area/vpcs/d77e1ab1-0320-4504-83c5-e78b431c7577"

# Request example:
```
```json
{
  "name": "my_updated_vpc",
  "description": "My prod VPC"
}
```
```go
resources, _ := ccaClient.GetResources("compute-on", "test_area")
ccaResources := resources.(cloudca.Resources)
updatedVpc, err := ccaResources.Vpcs.Update(cloudca.Vpc{
        Id: "d77e1ab1-0320-4504-83c5-e78b431c7577",
        Name: "my_updated_vpc",
        Description: "My prod VPC",
    })
```

<span class="method">PUT</span> <code>/services/<a href="#service-connections">:service_code</a>/<a href="#environments">:environment_name</a>/vpcs</code>

Update an existing VPC in your [environment](#environments)

Optional | Type | Description
-------- | ---- | -----------
`name` | *string* | The new name of the VPC
`description` | *string* | The new description of the VPC


<!-------------------- DELETE A VPC -------------------->


### Destroy a VPC


```shell

# Example:

curl -X DELETE \
   -H "MC-Api-Key: your_api_key" \
   "https://api.cloud.ca/v1/services/compute-on/test_area/vpcs/ad5bcae8-ee8b-4ee8-a7a4-381c25444b8e"
```
```go
resources, _ := ccaClient.GetResources("compute-on", "test_area")
ccaResources := resources.(cloudca.Resources)
success, err := ccaResources.Vpcs.Destroy("ad5bcae8-ee8b-4ee8-a7a4-381c25444b8e")
```

<span class="method">DELETE</span> <code>/services/<a href="#service-connections">:service_code</a>/<a href="#environments">:environment_name</a>/vpcs/:id</code>

Destroy an existing VPC. To delete a VPC, you must first delete all the [networks](#networks) in the VPC.

<!-------------------- RESTART A VPC -------------------->


### Restart a VPC


```shell

# Example:

curl -X POST \
   -H "MC-Api-Key: your_api_key" \
   "https://api.cloud.ca/v1/services/compute-on/test_area/vpcs/ad5bcae8-ee8b-4ee8-a7a4-381c25444b8e?operation=restart"
```
```go
resources, _ := ccaClient.GetResources("compute-on", "test_area")
ccaResources := resources.(cloudca.Resources)
success, err := ccaResources.Vpcs.RestartRouter("ad5bcae8-ee8b-4ee8-a7a4-381c25444b8e")
```

<span class="method">POST</span> <code>/services/<a href="#service-connections">:service_code</a>/<a href="#environments">:environment_name</a>/vpcs/:id?operation=restart</code>

Restart the router of a VPC.
