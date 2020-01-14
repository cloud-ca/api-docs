---
weight: 502
title: Networks
---

## Networks

A network is an isolated network with its own VLANs and CIDR list, where you can place groups of resources, such as [instances](#instances).

<!-------------------- LIST NETWORK -------------------->


### List networks

```shell
curl -X GET \
   -H "MC-Api-Key: your_api_key" \
   "https://api.cloud.ca/v1/services/compute-on/test_area/networks"

# Example response:
```
```json
{
  "data": [{
    "id": "8ef7539c-c9ba-49f3-a484-a08f4ffb2234",
    "name": "Frontend",
    "description": "default network",
    "vpcId": "12b8c150-b444-482a-8411-c08eaccb0a3b",
    "vpcName": "SomeVPC",
    "zoneId": "04afdbd1-e32d-4999-86d0-96703736dded",
    "zoneName": "QC-1",
    "cidr": "10.169.254.0/24",
    "gateway": "10.169.254.1",
    "netmask": "255.255.255.0",
    "networkAclId": "9ba3ec65-2e1d-11e4-8e05-42a29a39fc92",
    "networkAclName": "default_allow",
    "networkOfferingId": "9593f0df-573a-43c4-a107-a5c704a7cfee",
    "networkOfferingName": "Load Balanced Network",
    "networkOfferingDescription": "Offering for Isolated Vpc networks with Source Nat service enabled",
    "state": "Implemented"
  }],
  "metadata": {
    "recordCount": 1
  }
}
```
```go
resources, _ := ccaClient.GetResources("compute-on", "test_area")
ccaResources := resources.(cloudca.Resources)
networks, err := ccaResources.Networks.List()
```

<span class="method">GET</span> <code>/services/<a href="#service-connections">:service_code</a>/<a href="#environments">:environment_name</a>/networks</code>

Retrieve a list of all networks of an [environment](#environments)

Attributes | Type | Description
---------- | ---- | ------------
`id` | *UUID* | The id of the network
`name` | *string* | The name of the network
`description` | *string* | The description of the network
`vpcId` | *UUID* | The id of the [VPC](#vpcs) where the network was created
`vpcName` | *string* | The name of the [VPC](#vpcs) where the network was created
`zoneId` | *string* | The id of the [zone](#zones) where the network was created
`zoneName` | *string* | The name of the [zone](#zones) where the network was created
`cidr` | *string* | The cidr of the network
`gateway` | *string* | The gateway of the network
`netmask` | *string* | The netmask of the network
`networkAclId` | *UUID* | The id of the [network ACL](#network-acls) of the the network
`networkAclName` | *string* | The name of the [network ACL](#network-acls) of the the network
`networkOfferingId` | *UUID* | The id of the [network offering](#network-offerings) of the network
`networkOfferingName` | *string* | The name of the [network offering](#network-offerings) of the network
`networkOfferingDescription` | *string* | The description of the [network offering](#network-offerings) of the network
`state` | *string* | The state of the network. `Allocated` if no instances where created in the network yet, `Implemented` otherwise.

Query Parameters | Type | Description
---------------- | ---- | -----------
`vpc_id` | *UUID* | Filter the list to only retrieve the networks of a [VPC](#vpcs)
`zone_id` | *UUID* | Filter the list to only retrieve the networks in a specific [zone](#zones)


<!-------------------- RETRIEVE A NETWORK -------------------->


### Retrieve a network

```shell
curl -X GET \
   -H "MC-Api-Key: your_api_key" \
   "https://api.cloud.ca/v1/services/compute-on/test_area/networks/ad5bcae8-ee8b-4ee8-a7a4-381c25444b8e"

# Example response:
```
```json
{
  "data": {
    "id": "8ef7539c-c9ba-49f3-a484-a08f4ffb2234",
    "name": "Frontend",
    "description": "default network",
    "vpcId": "12b8c150-b444-482a-8411-c08eaccb0a3b",
    "vpcName": "SomeVPC",
    "zoneId": "04afdbd1-e32d-4999-86d0-96703736dded",
    "zoneName": "QC-1",
    "cidr": "10.169.254.0/24",
    "gateway": "10.169.254.1",
    "netmask": "255.255.255.0",
    "networkAclId": "9ba3ec65-2e1d-11e4-8e05-42a29a39fc92",
    "networkAclName": "default_allow",
    "networkOfferingId": "9593f0df-573a-43c4-a107-a5c704a7cfee",
    "networkOfferingName": "Load Balanced Network",
    "networkOfferingDescription": "Offering for Isolated Vpc networks with Source Nat service enabled",
    "state": "Implemented"
  }
}
```
```go
resources, _ := ccaClient.GetResources("compute-on", "test_area")
ccaResources := resources.(cloudca.Resources)
network, err := ccaResources.Networks.Get("ad5bcae8-ee8b-4ee8-a7a4-381c25444b8e")
```

<span class="method">GET</span> <code>/services/<a href="#service-connections">:service_code</a>/<a href="#environments">:environment_name</a>/networks/:id</code>

Retrieve information about a network.

Attributes | Type | Description
---------- | ---- | ------------
`id` | *UUID* | The id of the network
`name` | *string* | The name of the network
`description` | *string* | The description of the network
`vpcId` | *UUID* | The id of the [VPC](#vpcs) where the network was created
`vpcName` | *string* | The name of the [VPC](#vpcs) where the network was created
`zoneId` | *string* | The id of the [zone](#zones) where the network was created
`zoneName` | *string* | The name of the [zone](#zones) where the network was created
`cidr` | *string* | The cidr of the network
`gateway` | *string* | The gateway of the network
`netmask` | *string* | The netmask of the network
`networkAclId` | *UUID* | The id of the [network ACL](#network-acls) of the the network
`networkAclName` | *string* | The name of the [network ACL](#network-acls) of the the network
`networkOfferingId` | *UUID* | The id of the [network offering](#network-offerings) of the network
`networkOfferingName` | *string* | The name of the [network offering](#network-offerings) of the network
`networkOfferingDescription` | *string* | The description of the [network offering](#network-offerings) of the network
`state` | *string* | The state of the network. `Allocated` if no instances where created in the network yet, `Implemented` otherwise.


<!-------------------- CREATE A NETWORK -------------------->


### Create a network


```shell

# Example:

curl -X POST \
   -H "Content-Type: application/json" \
   -H "MC-Api-Key: your_api_key" \
   -d "request_body" \
   "https://api.cloud.ca/v1/services/compute-on/test_area/networks"

# Request example:
```
```json
{
  "name": "my_network",
  "description": "My production network",
  "vpcId": "b1932c7c-0b85-450f-92b9-bfdeb3e80804",
  "networkOfferingId": "c5d4ffcd-56e2-407a-8b4d-06082b7365c4",
  "networkAclId": "9ba3ec65-2e1d-11e4-8e05-42a29a39fc92"
}
```
```go
resources, _ := ccaClient.GetResources("compute-on", "test_area")
ccaResources := resources.(cloudca.Resources)
createdNetwork, err := ccaResources.Networks.Create(cloudca.Network{
        Name: "my_network",
        Description: "My production network",
        VpcId: "b1932c7c-0b85-450f-92b9-bfdeb3e80804",
        NetworkOfferingId: "c5d4ffcd-56e2-407a-8b4d-06082b7365c4",
        NetworkAclId: "9ba3ec65-2e1d-11e4-8e05-42a29a39fc92"
    },  map[string]string{})
```
```dart
resource "cloudca_network" "my_network" {
    service_code = "compute-on"
    environment_name = "test_area"
    name = "my_network"
    description = "This is a prod network"
    vpc_id = "8b46e2d1-bbc4-4fad-b3bd-1b25fcba4cec"
    network_offering = "Standard Network"
    network_acl_id = "7d428416-263d-47cd-9270-2cdbdf222f57"
}
```

<span class="method">POST</span> <code>/services/<a href="#service-connections">:service_code</a>/<a href="#environments">:environment_name</a>/networks</code>

Create a network in an [environment](#environments)

Required | Type | Description
-------- | ---- | -----------
`name` | *string* | The name of the new network
`description` | *string* | The description of the new network
`vpcId` | *UUID* | The id of the VPC where to create the network
`networkOfferingId` | *UUID* | The id of the [network offering](#network-offerings) to use for the network
`networkAclId` | *UUID* | The id of the [network ACL](#network-acls) to use for the network


<!-------------------- UPDATE A NETWORK -------------------->


### Update a network


```shell

# Example:

curl -X PUT \
   -H "Content-Type: application/json" \
   -H "MC-Api-Key: your_api_key" \
   -d "request_body" \
   "https://api.cloud.ca/v1/services/compute-on/test_area/networks/9572d2ea-a60d-478a-a75e-8ed31f2641f1"

# Request example:
```
```json
{
  "name": "my_updated_network",
  "description": "My updated production network"
}
```
```go
resources, _ := ccaClient.GetResources("compute-on", "test_area")
ccaResources := resources.(cloudca.Resources)
updatedNetwork, err := ccaResources.Networks.Update("9572d2ea-a60d-478a-a75e-8ed31f2641f1", cloudca.Network{
        Name: "my_updated_network",
        Description: "My updated production network"
    })
```

<span class="method">POST</span> <code>/services/<a href="#service-connections">:service_code</a>/<a href="#environments">:environment_name</a>/networks/9572d2ea-a60d-478a-a75e-8ed31f2641f1</code>

Update an existing network in an [environment](#environments)

Required | Type | Description
-------- | ---- | -----------
`name` | *string* | The updated name of the network
`description` | *string* | The updated description of the network


<!-------------------- DELETE A NETWORK -------------------->


### Delete a network


```shell

# Example:

curl -X DELETE \
   -H "MC-Api-Key: your_api_key" \
   "https://api.cloud.ca/v1/services/compute-on/test_area/networks/9572d2ea-a60d-478a-a75e-8ed31f2641f1"
```
```go
resources, _ := ccaClient.GetResources("compute-on", "test_area")
ccaResources := resources.(cloudca.Resources)
success, err := ccaResources.Networks.Delete("9572d2ea-a60d-478a-a75e-8ed31f2641f1")
```

<span class="method">POST</span> <code>/services/<a href="#service-connections">:service_code</a>/<a href="#environments">:environment_name</a>/networks/9572d2ea-a60d-478a-a75e-8ed31f2641f1</code>

Delete an existing network in an [environment](#environments) To delete a network, you must first delete all the [instances](#instances) in the network.


<!-------------------- REPLACE THE NETWORK ACL OF A NETWORK -------------------->


### Replace the network ACL


```shell

# Example:

curl -X POST \
   -H "Content-Type: application/json" \
   -H "MC-Api-Key: your_api_key" \
   -d "request_body" \
   "https://api.cloud.ca/v1/services/compute-on/test_area/networks/9572d2ea-a60d-478a-a75e-8ed31f2641f1?operation=replace"

# Request example:
```
```json
{
  "name": "my_updated_network",
  "description": "My updated production network"
}
```
```go
resources, _ := ccaClient.GetResources("compute-on", "test_area")
ccaResources := resources.(cloudca.Resources)
success, err := ccaResources.Networks.ChangeAcl("9572d2ea-a60d-478a-a75e-8ed31f2641f1", "9ba3863e-2e1d-11e4-8e05-42a29a39fc92")
```

<span class="method">POST</span> <code>/services/<a href="#service-connections">:service_code</a>/<a href="#environments">:environment_name</a>/networks/9572d2ea-a60d-478a-a75e-8ed31f2641f1?operation=replace</code>

Replace the [network ACL](#network-acls).

Required | Type | Description
-------- | ---- | -----------
`networkAclId` | *string* | The id of the [network ACL](#network-acls) to use for the network
