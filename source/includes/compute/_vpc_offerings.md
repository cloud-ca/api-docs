### VPC offerings

VPC offerings determine which services are available to provisioned VPCs.

#### List VPC offerings

```shell
curl -X GET -H "MC-Api-Key: [your-api-key]"
"https://api.cloud.ca/v1/services/compute-qc/test_area/vpcofferings"

# The above command returns JSON structured like this:
```
```json
{
    "data": [
        {
            "id": "21a40b85-5fa9-440f-ab77-5e560073b584",
            "name": "Default VPC offering",
            "services": [
                "PortForwarding",
                "Lb",
                "NetworkACL",
                "SourceNat",
                "Dns",
                "StaticNat",
                "Vpn",
                "Dhcp",
                "UserData"
            ],
            "state": "Enabled"
        }
    ],
    "metadata": {
        "recordCount": 1
    }
}
```
```go
resources, _ := ccaClient.GetResources("compute-qc", "test_area")
ccaResources := resources.(cloudca.Resources)
vpcOfferings, _ := ccaResources.VpcOfferings.List()
```

<code>GET https://api.cloud.ca/v1/services/<a href="#service-connections">:service_code</a>/<a href="#environments">:environment_name</a>/vpcofferings</code>

Retrieve a list of available VPC offerings.

Attributes | &nbsp;
---------- | -----
id<br/>*UUID* | ---
name<br/>*string* | ---
services<br/>*Array[string]* | The services provided by the offering
state<br/>*string* | The state of the offering

#### Retrieve a VPC offering

```shell
curl -X GET -H "MC-Api-Key: [your-api-key]"
"https://api.cloud.ca/v1/services/compute-qc/test_area/vpcofferings/21a40b85-5fa9-440f-ab77-5e560073b584"

# The above command returns JSON structured like this:
```
```json
{
    "data": {
        "id": "21a40b85-5fa9-440f-ab77-5e560073b584",
        "name": "Default VPC offering",
        "services": [
            "PortForwarding",
            "Lb",
            "NetworkACL",
            "SourceNat",
            "Dns",
            "StaticNat",
            "Vpn",
            "Dhcp",
            "UserData"
        ],
        "state": "Enabled"
    }
}
```
```go
resources, _ := ccaClient.GetResources("compute-qc", "test_area")
ccaResources := resources.(cloudca.Resources)
vpcOfferings, _ := ccaResources.VpcOfferings.Get("21a40b85-5fa9-440f-ab77-5e560073b584")
```

<code>GET https://api.cloud.ca/v1/services/<a href="#service-connections">:service_code</a>/<a href="#environments">:environment_name</a>/vpcofferings/:id</code>

Retrieve a VPC offering.

Attributes | &nbsp;
---------- | -----
id<br/>*UUID* | ---
name<br/>*string* | ---
services<br/>*Array[string]* | The services provided by the offering
state<br/>*string* | The state of the offering
