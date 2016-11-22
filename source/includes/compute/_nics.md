### NICs


<!-------------------- LIST NICS -------------------->


#### List NICs


```shell
curl -X GET -H "MC-Api-Key: your_api_key"
"https://api.cloud.ca/v1/services/compute-qc/prod/nics"

# Example response:
```
```json
{
  "data": [{
    "id": "fff1f45a-8350-4c87-be43-947b96d01ebd",
    "name": "NIC-0",
    "ipAddress": "10.169.253.165",
    "isDefault": true,
    "networkId": "d2243d4c-0dd8-4f8c-9ab4-4b1d285d5642",
    "networkName": "Backend",
    "gateway": "10.169.253.1",
    "netmask": "255.255.255.0",
    "instanceId": "b6145e8b-abd3ta-456c-832c-f3db86a6acfe",
    "vpcId": "5aa9f5d7-55a9-43bf-bd2c-78a6bae1b267",
    "vpcName": "default-vpc",
    "secondaryIps": [
      {
        "id": "9c28e297-5d23-41a3-a167-34dc24f1df19",
        "ipAddress": "10.169.253.124"
      }
    ]
  }],
  "metadata": {
    "recordCount": 1
  }
}
```

<code>GET <a href="#service-connections">:service_code</a>/<a href="#environments">:environment_name</a>/portforwardingrules</code>

Retrieve a list of all NICs.

Attributes | &nbsp;
---------- | -----
`id`<br/>*UUID* | The id of the port forwarding rule
`name`<br/>*string* | The name of the NIC
`ipAddress`<br/>*string* | The IP address of the NIC
`isDefault`<br/>*string* | true if it's the default NIC of the [instance](#instances) (i.e. it will be the private IP on the instance)
`networkId`<br/>*UUID* | The id of the [tier](#tiers) of the NIC
`networkName`<br/>*string* | The name of the [tier](#tiers) of the NIC
`gateway`<br/>*string* | The gateway of the [tier](#tiers) associated with the NIC
`netmask`<br/>*string* | The netmask of the [tier](#tiers) associated with the NIC
`instanceId`<br/>*string* | The id of the instance associated with the NIC
`vpcId`<br/>*string* | The id of the VPC associated with the NIC
`vpcName`<br/>*string* | The name of the VPC associated with the NIC
`secondaryIps`<br/>*[SecondaryIP](#list-secondary-ips)* | The list of secondary IPs of the NIC<br/>*includes:* `id`, `ipAddress`


<!-------------------- RETRIEVE A NIC -------------------->


#### Retrieve a NIC


```shell
curl -X GET -H "MC-Api-Key: your_api_key"
"https://api.cloud.ca/v1/services/compute-qc/prod/nics/fff1f45a-8350-4c87-be43-947b96d01ebd"

# Example response:
```
```json
{
  "data": {
    "id": "fff1f45a-8350-4c87-be43-947b96d01ebd",
    "name": "NIC-0",
    "ipAddress": "10.169.253.165",
    "isDefault": true,
    "networkId": "d2243d4c-0dd8-4f8c-9ab4-4b1d285d5642",
    "networkName": "Backend",
    "gateway": "10.169.253.1",
    "netmask": "255.255.255.0",
    "instanceId": "b6145e8b-abd3ta-456c-832c-f3db86a6acfe",
    "vpcId": "5aa9f5d7-55a9-43bf-bd2c-78a6bae1b267",
    "vpcName": "default-vpc",
    "secondaryIps": [
      {
        "id": "9c28e297-5d23-41a3-a167-34dc24f1df19",
        "ipAddress": "10.169.253.124"
      }
    ]
  }
}
```

<code>GET /services/<a href="#service-connections">:service_code</a>/<a href="#environments">:environment_name</a>/nics/:id</code>

Retrieve an existing NIC.

Attributes | &nbsp;
---------- | -----
`id`<br/>*UUID* | The id of the port forwarding rule
`name`<br/>*string* | The name of the NIC
`ipAddress`<br/>*string* | The IP address of the NIC
`isDefault`<br/>*string* | true if it's the default NIC of the [instance](#instances) (i.e. it will be the private IP on the instance)
`networkId`<br/>*UUID* | The id of the [tier](#tiers) of the NIC
`networkName`<br/>*string* | The name of the [tier](#tiers) of the NIC
`gateway`<br/>*string* | The gateway of the [tier](#tiers) associated with the NIC
`netmask`<br/>*string* | The netmask of the [tier](#tiers) associated with the NIC
`instanceId`<br/>*string* | The id of the instance associated with the NIC
`vpcId`<br/>*string* | The id of the VPC associated with the NIC
`vpcName`<br/>*string* | The name of the VPC associated with the NIC
`secondaryIps`<br/>*[SecondaryIP](#list-secondary-ips)* | The list of secondary IPs of the NIC<br/>*includes:* `id`, `ipAddress`


<!-------------------- CREATE A NIC -------------------->


#### Create a NIC


```shell

# Example:

curl -X POST -H "Content-Type: application/json" -H "MC-Api-Key: your-api-key" -d "{
  \"networkId\" : \"\",
  \"instanceId\" : \"\"
}" "https://api.cloud.ca/v1/services/compute-qc/prod/nics"

# Request example:
```
```json
{
  "networkId": "6ffc3de2-d086-41d6-bc4d-d2d02566b3cf",
  "instanceId": ""
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

<code>POST /services/<a href="#service-connections">:service_code</a>/<a href="#environments">:environment_name</a>/tiers</code>

Create a tier in an environment.

Required | &nbsp;
------ | -----------
`name`<br/>*string* | The name of the new tier
`description`<br/>*string* | The description of the new tier
`vpcId`<br/>*UUID* | The id of the VPC where to create the tier
`networkOfferingId`<br/>*UUID* | The id of the [network offering](#network-offerings) to use for the tier
`networkAclId`<br/>*UUID* | The id of the [network ACL](#network-acls) to use for the tier
