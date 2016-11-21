### Network offerings

Network offerings determine which services are available to each provisioned tier.

#### List network offerings

```shell
curl -X GET -H "MC-Api-Key: [your-api-key]"
"https://api.cloud.ca/v1/services/compute-on/test_area/networkofferings"

# The above command returns JSON structured like this:
```
```json
{
    "data": [
        {
            "id": "89724d35-b69c-418c-be81-7d83fcfc9da9",
            "name": "Load Balanced Tier",
            "services": [
                "PortForwarding",
                "Vpn",
                "SourceNat",
                "Dhcp",
                "NetworkACL",
                "Dns",
                "Lb",
                "UserData",
                "StaticNat"
            ],
            "state": "ENABLED"
        },
        {
            "id": "087502ea-cb42-421b-9bd9-9cf9ae5d1b89",
            "name": "Standard Tier",
            "services": [
                "PortForwarding",
                "Vpn",
                "SourceNat",
                "Dhcp",
                "NetworkACL",
                "Dns",
                "UserData",
                "StaticNat"
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
resources, _ := ccaClient.GetResources("compute-on", "test_area")
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
"https://api.cloud.ca/v1/services/compute-on/test_area/networkofferings/89724d35-b69c-418c-be81-7d83fcfc9da9"

# The above command returns JSON structured like this:
```
```json
{
    "data": {
        "id": "89724d35-b69c-418c-be81-7d83fcfc9da9",
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
resources, _ := ccaClient.GetResources("compute-on", "test_area")
ccaResources := resources.(cloudca.Resources)
networkOfferings, _ := ccaResources.NetworkOfferings.Get("89724d35-b69c-418c-be81-7d83fcfc9da9")
```

<code>GET https://api.cloud.ca/v1/services/<a href="#service-connections">:service_code</a>/<a href="#environments">:environment_name</a>/networkofferings/:id</code>

Retrieve a network offering.

Attributes | &nbsp;
---------- | -----
id<br/>*UUID* | ---
name<br/>*string* | ---
services<br/>*Array[string]* | The services provided by the offering
state<br/>*string* | The state of the offering
