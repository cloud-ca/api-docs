### Tiers

A tier is an isolated network with its own VLANs and CIDR list, where you can place groups of resources, such as instances.

<!-------------------- LIST TIER -------------------->


#### List tiers

```shell
curl -X GET -H "MC-Api-Key: [your-api-key]"
"https://api.cloud.ca/v1/services/compute-qc/prod/tiers"

# Example response:
```
```json
{
  "data": [{
    "id": "8ef7539c-c9ba-49f3-a484-a08f4ffb2234",
    "name": "Frontend",
    "description": "default tier",
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
    "networkOfferingName": "Load Balanced Tier",
    "networkOfferingDescription": "Offering for Isolated Vpc networks with Source Nat service enabled",
    "state": "Implemented"
  }],
  "metadata": {
    "recordCount": 1
  }
}
```
```go
resources, _ := ccaClient.GetResources("compute-qc", "prod")
ccaResources := resources.(cloudca.Resources)
tiers, err := ccaResources.Tiers.List()
```

<code>GET https://api.cloud.ca/v1/services/<a href="#service-connections">:service_code</a>/<a href="#environments">:environment_name</a>/tiers</code>

Retrieve a list of all tiers of an environment.

Attributes | &nbsp;
---------- | -----
`id`<br/>*UUID* | The id of the tier
`name`<br/>*string* | The name of the tier
`description`<br/>*string* | The description of the tier
`vpcId`<br/>*UUID* | The id of the [VPC](#vpcs) where the tier was created
`vpcName`<br/>*string* | The name of the [VPC](#vpcs) where the tier was created
`zoneId`<br/>*string* | The id of the [zone](#zones) where the tier was created
`zoneName`<br/>*string* | The name of the [zone](#zones) where the tier was created
`cidr`<br/>*string* | The cidr of the tier
`gateway`<br/>*string* | The gateway of the tier
`netmask`<br/>*string* | The netmask of the tier
`networkAclId`<br/>*UUID* | The id of the [network ACL](#network-acls) of the the tier
`networkAclName`<br/>*string* | The name of the [network ACL](#network-acls) of the the tier
`networkOfferingId`<br/>*UUID* | The id of the [network offering](#network-offerings) of the tier
`networkOfferingName`<br/>*string* | The name of the [network offering](#network-offerings) of the tier
`networkOfferingDescription`<br/>*string* | The description of the [network offering](#network-offerings) of the tier
`state`<br/>*string* | The state of the tier. `Allocated` if no instances where created in the tier yet, `Implemented` otherwise.


<!-------------------- RETRIEVE A TIER -------------------->


#### Retrieve a tier

```shell
curl -X GET -H "MC-Api-Key: [your-api-key]"
"https://api.cloud.ca/v1/services/compute-qc/prod/tiers/ad5bcae8-ee8b-4ee8-a7a4-381c25444b8e"

# Example response:
```
```json
{
  "data": {
    "id": "8ef7539c-c9ba-49f3-a484-a08f4ffb2234",
    "name": "Frontend",
    "description": "default tier",
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
    "networkOfferingName": "Load Balanced Tier",
    "networkOfferingDescription": "Offering for Isolated Vpc networks with Source Nat service enabled",
    "state": "Implemented"
  }
}
```
```go
resources, _ := ccaClient.GetResources("compute-qc", "prod")
ccaResources := resources.(cloudca.Resources)
tier, err := ccaResources.Tiers.Get("ad5bcae8-ee8b-4ee8-a7a4-381c25444b8e")
```

<code>GET https://api.cloud.ca/v1/services/<a href="#service-connections">:service_code</a>/<a href="#environments">:environment_name</a>/tiers/:id</code>

Retrieve information about a tier.

Attributes | &nbsp;
---------- | -----
`id`<br/>*UUID* | The id of the tier
`name`<br/>*string* | The name of the tier
`description`<br/>*string* | The description of the tier
`vpcId`<br/>*UUID* | The id of the [VPC](#vpcs) where the tier was created
`vpcName`<br/>*string* | The name of the [VPC](#vpcs) where the tier was created
`zoneId`<br/>*string* | The id of the [zone](#zones) where the tier was created
`zoneName`<br/>*string* | The name of the [zone](#zones) where the tier was created
`cidr`<br/>*string* | The cidr of the tier
`gateway`<br/>*string* | The gateway of the tier
`netmask`<br/>*string* | The netmask of the tier
`networkAclId`<br/>*UUID* | The id of the [network ACL](#network-acls) of the the tier
`networkAclName`<br/>*string* | The name of the [network ACL](#network-acls) of the the tier
`networkOfferingId`<br/>*UUID* | The id of the [network offering](#network-offerings) of the tier
`networkOfferingName`<br/>*string* | The name of the [network offering](#network-offerings) of the tier
`networkOfferingDescription`<br/>*string* | The description of the [network offering](#network-offerings) of the tier
`state`<br/>*string* | The state of the tier. `Allocated` if no instances where created in the tier yet, `Implemented` otherwise.


<!-------------------- CREATE A TIER -------------------->


#### Create a tier


```shell

# Example:

curl -X POST -H "Content-Type: application/json" -H "MC-Api-Key: [your-api-key]" -d "{
  \"name\" : \"my_tier\",
  \"description\" : \"My production tier\",
  \"vpcId\": \"b1932c7c-0b85-450f-92b9-bfdeb3e80804\",
  \"networkOfferingId\" : \"c5d4ffcd-56e2-407a-8b4d-06082b7365c4\",
  \"networkAclId\" : \"9ba3ec65-2e1d-11e4-8e05-42a29a39fc92\"
}" "https://api.cloud.ca/v1/services/compute-qc/prod/tiers"

# Request example:
```
```json
{
  "name": "my_tier",
  "description": "My production tier",
  "vpcId": "b1932c7c-0b85-450f-92b9-bfdeb3e80804",
  "networkOfferingId": "c5d4ffcd-56e2-407a-8b4d-06082b7365c4",
  "networkAclId": "9ba3ec65-2e1d-11e4-8e05-42a29a39fc92"
}
```
```go
resources, _ := ccaClient.GetResources("compute-qc", "prod")
ccaResources := resources.(cloudca.Resources)
createdTier, err := ccaResources.Tiers.Create(cloudca.Tier{
        Name: "my_tier",
        Description: "My production tier",
        VpcId: "b1932c7c-0b85-450f-92b9-bfdeb3e80804",
        NetworkOfferingId: "c5d4ffcd-56e2-407a-8b4d-06082b7365c4",
        NetworkAclId: "9ba3ec65-2e1d-11e4-8e05-42a29a39fc92"
    },  map[string]string{})
```
```dart
resource "cloudca_tier" "my_tier" {
    service_code = "compute-qc"
    environment_name = "prod"
    name = "my_tier"
    description = "This is a prod tier"
    vpc_id = "8b46e2d1-bbc4-4fad-b3bd-1b25fcba4cec"
    network_offering = "Standard Tier"
    network_acl_id = "7d428416-263d-47cd-9270-2cdbdf222f57"
}
```

<code>POST https://api.cloud.ca/v1/services/<a href="#service-connections">:service_code</a>/<a href="#environments">:environment_name</a>/tiers</code>

Create a tier in an environment.

Required | &nbsp;
------ | -----------
`name`<br/>*string* | The name of the new tier
`description`<br/>*string* | The description of the new tier
`vpcId`<br/>*UUID* | The id of the VPC where to create the tier
`networkOfferingId`<br/>*UUID* | The id of the [network offering](#network-offerings) to use for the tier
`networkAclId`<br/>*UUID* | The id of the [network ACL](#network-acls) to use for the tier


<!-------------------- UPDATE A TIER -------------------->


#### Update a tier


```shell

# Example:

curl -X PUT -H "Content-Type: application/json" -H "MC-Api-Key: [your-api-key]" -d "{
  \"name\" : \"my_updated_tier\",
  \"description\" : \"My updated production tier\"
}" "https://api.cloud.ca/v1/services/compute-qc/prod/tiers/9572d2ea-a60d-478a-a75e-8ed31f2641f1"

# Request example:
```
```json
{
  "name": "my_updated_tier",
  "description": "My updated production tier"
}
```
```go
resources, _ := ccaClient.GetResources("compute-qc", "prod")
ccaResources := resources.(cloudca.Resources)
updatedTier, err := ccaResources.Tiers.Update("9572d2ea-a60d-478a-a75e-8ed31f2641f1", cloudca.Tier{
        Name: "my_updated_tier",
        Description: "My updated production tier"
    })
```

<code>POST https://api.cloud.ca/v1/services/<a href="#service-connections">:service_code</a>/<a href="#environments">:environment_name</a>/tiers/9572d2ea-a60d-478a-a75e-8ed31f2641f1</code>

Update an existing tier in an environment.

Required | &nbsp;
------ | -----------
`name`<br/>*string* | The updated name of the tier
`description`<br/>*string* | The updated description of the tier


<!-------------------- DELETE A TIER -------------------->


#### Delete a tier


```shell

# Example:

curl -X DELETE -H "MC-Api-Key: [your-api-key]" "https://api.cloud.ca/v1/services/compute-qc/prod/tiers/9572d2ea-a60d-478a-a75e-8ed31f2641f1"
```
```go
resources, _ := ccaClient.GetResources("compute-qc", "prod")
ccaResources := resources.(cloudca.Resources)
success, err := ccaResources.Tiers.Delete("9572d2ea-a60d-478a-a75e-8ed31f2641f1")
```

<code>POST https://api.cloud.ca/v1/services/<a href="#service-connections">:service_code</a>/<a href="#environments">:environment_name</a>/tiers/9572d2ea-a60d-478a-a75e-8ed31f2641f1</code>

Delete an existing tier in an environment. To delete a tier, you must first delete all the [instances](#instances) in the tier.


<!-------------------- REPLACE THE NETWORK ACL OF A TIER -------------------->


#### Replace the network ACL of a tier


```shell

# Example:

curl -X POST -H "Content-Type: application/json" -H "MC-Api-Key: [your-api-key]" -d "{
  \"networkAclId\" : \"9ba3863e-2e1d-11e4-8e05-42a29a39fc92\"
}" "https://api.cloud.ca/v1/services/compute-qc/prod/tiers/9572d2ea-a60d-478a-a75e-8ed31f2641f1?operation=replace"

# Request example:
```
```json
{
  "name": "my_updated_tier",
  "description": "My updated production tier"
}
```
```go
resources, _ := ccaClient.GetResources("compute-qc", "prod")
ccaResources := resources.(cloudca.Resources)
success, err := ccaResources.Tiers.ChangeAcl("9572d2ea-a60d-478a-a75e-8ed31f2641f1", "9ba3863e-2e1d-11e4-8e05-42a29a39fc92")
```

<code>POST https://api.cloud.ca/v1/services/<a href="#service-connections">:service_code</a>/<a href="#environments">:environment_name</a>/tiers/9572d2ea-a60d-478a-a75e-8ed31f2641f1?operation=replace</code>

Replace the network ACL of an existing tier.

Required | &nbsp;
------ | -----------
`networkAclId`<br/>*string* | The id of the network ACL to use for the tier
