---
weight: 508
title: Remote access VPNs
---

## Remote access VPNs

Remote access VPNs allow users to connect to [VPCs](#vpcs) through secure connections.

### List remote access VPNs

```shell
curl -H "MC-Api-Key: your_api_key" \
   "https://api.cloud.ca/v1/services/compute-on/test_area/remoteaccessvpns"

# Response example:
```
```json
{
    "data": [
        {
            "id": "10001e7d-b4ef-489b-836e-0619a383bc8d",
            "publicIpAddress": "69.196.164.31",
            "publicIpAddressId": "10001e7d-b4ef-489b-836e-0619a383bc8d",
            "state": "Disabled"
        },
        {
            "id": "8925406c-8051-467e-a0ca-c48caa5bf670",
            "presharedKey": "Kwth4JYUfXXmtMG4X7vAwRPH",
            "publicIpAddress": "69.196.164.223",
            "publicIpAddressId": "8925406c-8051-467e-a0ca-c48caa5bf670",
            "state": "Enabled"
        }
    ],
    "metadata": {
        "recordCount": 2
    }
}
```

<span class="method">GET</span> <code>/services/<a href="#service-connections">:service_code</a>/<a href="#environments">:environment_name</a>/remoteaccessvpns</code>

List remote access VPNs.

Attributes | Type | Description
-------------- | ---- | ------------
`id` | *UUID* | The id of the remote access VPN
`presharedKey` | *string* | The VPN's preshared key
`publicIpAddress` | *string* | The [public IP](#public-ips) (e.g. 208.80.154.224)
`publicIpAddressId` | *string* | The id of the [public IP](#public-ips)
`state` | *string* | The state.<br/>*Possible values:* `Enabled`, `Disabled.`

Query Parameters | &nbsp;
-------------- | ---- | ------------
`vpc_id` | *UUID* | Filter the list to only retrieve the VPN information of a specific [VPC](#vpcs)

### Retrieve a remote access VPN
```shell
curl -H "MC-Api-Key: your_api_key" \
   "https://api.cloud.ca/v1/services/compute-on/test_area/remoteaccessvpns/10001e7d-b4ef-489b-836e-0619a383bc8d"

# Response example:
```
```json
{
    "data": {
        "id": "10001e7d-b4ef-489b-836e-0619a383bc8d",
        "publicIpAddress": "69.196.164.31",
        "publicIpAddressId": "10001e7d-b4ef-489b-836e-0619a383bc8d",
        "state": "Disabled"
    }
}
```

<span class="method">GET</span> <code>/services/<a href="#service-connections">:service_code</a>/<a href="#environments">:environment_name</a>/remoteaccessvpns/:id</code>

Retrieve a remote access VPN.

Attributes | Type | Description
-------------- | ---- | ------------
`id` | *UUID* | The id of the remote access VPN
`presharedKey` | *string* | The VPN's preshared key
`publicIpAddress` | *string* | The [public IP](#public-ips) (e.g. 208.80.154.224)
`publicIpAddressId` | *string* | The id of the [public IP](#public-ips)
`state` | *string* | The state.<br/>*Possible values:* `Enabled`, `Disabled.`
