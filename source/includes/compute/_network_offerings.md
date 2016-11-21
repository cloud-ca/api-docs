### Network offerings

Network offerings determine which services are available to each provisioned tier.

#### List network offerings

```shell
curl -X GET -H "MC-Api-Key: [your-api-key]"
"https://api.cloud.ca/v1/services/compute-qc/test_area/networkofferings"

# The above command returns JSON structured like this:
```
```json
{
    "data": [
        {
            "id": "9593f0df-573a-43c4-a107-a5c704a7cfee",
            "name": "Load Balanced Tier",
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
            "state": "ENABLED"
        },
        {
            "id": "c5d4ffcd-56e2-407a-8b4d-06082b7365c4",
            "name": "Standard Tier",
            "services": [
                "PortForwarding",
                "NetworkACL",
                "SourceNat",
                "Dns",
                "StaticNat",
                "Vpn",
                "Dhcp",
                "UserData"
            ],
            "state": "ENABLED"
        }
    ],
    "metadata": {
        "recordCount": 2
    }
}
```
```go
resources, _ := ccaClient.GetResources("compute-qc", "test_area")
ccaResources := resources.(cloudca.Resources)
networkOfferings, _ := ccaResources.NetworkOfferings.List()
```

<code>GET https://api.cloud.ca/v1/services/<a href="#service-connections">:service_code</a>/<a href="#environments">:environment_name</a>/networkofferings</code>

Retrieve a list of available network offerings.

Attributes | &nbsp;
---------- | -----
id<br/>*UUID* | ---
name<br/>*string* | ---
services<br/>*Array[string]* | The services provided by the offering
state<br/>*string* | The state of the offering

#### Retrieve a network offering

```shell
curl -X GET -H "MC-Api-Key: [your-api-key]"
"https://api.cloud.ca/v1/services/compute-qc/test_area/networkofferings/9593f0df-573a-43c4-a107-a5c704a7cfee"

# The above command returns JSON structured like this:
```
```json
{
    "data": {
        "id": "9593f0df-573a-43c4-a107-a5c704a7cfee",
        "name": "Load Balanced Tier",
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
        "state": "ENABLED"
    }
}
```
```go
resources, _ := ccaClient.GetResources("compute-qc", "test_area")
ccaResources := resources.(cloudca.Resources)
networkOfferings, _ := ccaResources.NetworkOfferings.Get("9593f0df-573a-43c4-a107-a5c704a7cfee")
```

<code>GET https://api.cloud.ca/v1/services/<a href="#service-connections">:service_code</a>/<a href="#environments">:environment_name</a>/networkofferings/:id</code>

Retrieve a network offering.

Attributes | &nbsp;
---------- | -----
id<br/>*UUID* | ---
name<br/>*string* | ---
services<br/>*Array[string]* | The services provided by the offering
state<br/>*string* | The state of the offering
