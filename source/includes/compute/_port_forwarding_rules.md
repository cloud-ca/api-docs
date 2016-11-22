### Port forwarding rules

<!-------------------- LIST PORT FORWARDING RULES -------------------->

#### List port forwarding rules

```shell
curl -X GET -H "MC-Api-Key: [your-api-key]"
"https://api.cloud.ca/v1/services/compute-qc/prod/portforwardingrules"

# Example response:
```
```json
{
  "data": [{
    "id": "bf145d1e-7beb-42b8-bd2c-1a316aeb9aef",
    "ipAddress": "74.121.244.23",
    "ipAddressId": "747e30d0-a0cd-48ba-b7d8-77a2f7e10504",
    "privatePortStart": "8080",
    "privatePortEnd": "8080",
    "publicPortStart": "80",
    "publicPortEnd": "80",
    "protocol": "TCP",
    "instanceId": "d7328dd9-882e-4d08-8ad2-c74c2d493689",
    "instanceName": "my_app_instance",
    "networkId": "7388f551-4163-4467-b49b-58e9310d7207",
    "vpcId": "39907f0a-c253-42b8-b02d-337e00e9851e",
    "privateIp": "10.155.24.145",
    "privateIpId": "10.155.24.145	"
  }],
  "metadata": {
    "recordCount": 1
  }
}
```
```go
resources, _ := ccaClient.GetResources("compute-qc", "prod")
ccaResources := resources.(cloudca.Resources)
portForwardingRules, err := ccaResources.PortForwardingRules.List()
```

<code>GET https://api.cloud.ca/v1/services/<a href="#service-connections">:service_code</a>/<a href="#environments">:environment_name</a>/portforwardingrules</code>

Retrieve a list of all port forwarding rules of an environment.

Attributes | &nbsp;
---------- | -----
`id`<br/>*UUID* | The id of the port forwarding rule
`ipAddress`<br/>*string* | The ip address of the [public IP](#public-ips) associated to this port forwarding rule
`ipAddressId`<br/>*UUID* | The id of the [public IP](#public-ips) associated to this port forwarding rule
`privatePortStart`<br/>*string* | The start of the private port range
`privatePortEnd`<br/>*string* | The end of the private port range
`publicPortStart`<br/>*string* | The start of the public port range
`publicPortEnd`<br/>*string* | The end of the public port range
`protocol`<br/>*string* | The protocol of the port forwarding rule (e.g. TCP, UDP)
`instanceId`<br/>*UUID* | The id of the [instance](#instances) of the port forwarding rule
`instanceName`<br/>*string* | The name of the [instance](#instances) of the port forwarding rule
`networkId`<br/>*UUID* | The id of the [tier](#tiers) of the port forwarding rule
`vpcId`<br/>*UUID* | The id of the [VPC](#vpcs) of the port forwarding rule
`privateIp`<br/>*string* | The private IP address of the instance where requests will be forwarded
`privateIpId`<br/>*UUID* | The id of private IP address of the instance where requests will be forwarded

<!-------------------- RETRIEVE A PORT FORWARDING RULE -------------------->


#### Retrieve a port forwarding rule

```shell
curl -X GET -H "MC-Api-Key: [your-api-key]"
"https://api.cloud.ca/v1/services/compute-qc/prod/portforwardingrules/ad5bcae8-ee8b-4ee8-a7a4-381c25444b8e"

# Example response:
```
```json
{
  "data": {
    "id": "bf145d1e-7beb-42b8-bd2c-1a316aeb9aef",
    "ipAddress": "74.121.244.23",
    "ipAddressId": "747e30d0-a0cd-48ba-b7d8-77a2f7e10504",
    "privatePortStart": "8080",
    "privatePortEnd": "8080",
    "publicPortStart": "80",
    "publicPortEnd": "80",
    "protocol": "TCP",
    "instanceName": "my_app_instance",
    "instanceId": "d7328dd9-882e-4d08-8ad2-c74c2d493689",
    "networkId": "7388f551-4163-4467-b49b-58e9310d7207",
    "vpcId": "39907f0a-c253-42b8-b02d-337e00e9851e",
    "privateIp": "10.155.24.145",
    "privateIpId": "10.155.24.145"
  }
}
```
```go
resources, _ := ccaClient.GetResources("compute-qc", "prod")
ccaResources := resources.(cloudca.Resources)
portForwardingRule, err := ccaResources.PortForwardingRule.Get("bf145d1e-7beb-42b8-bd2c-1a316aeb9aef")
```

<code>GET https://api.cloud.ca/v1/services/<a href="#service-connections">:service_code</a>/<a href="#environments">:environment_name</a>/portforwardingrules/:id</code>

Retrieve information about a port forwarding rule.

Attributes | &nbsp;
---------- | -----
`id`<br/>*UUID* | The id of the port forwarding rule
`ipAddress`<br/>*string* | The ip address of the [public IP](#public-ips) associated to this port forwarding rule
`ipAddressId`<br/>*UUID* | The id of the [public IP](#public-ips) associated to this port forwarding rule
`privatePortStart`<br/>*string* | The start of the private port range
`privatePortEnd`<br/>*string* | The end of the private port range
`publicPortStart`<br/>*string* | The start of the public port range
`publicPortEnd`<br/>*string* | The end of the public port range
`protocol`<br/>*string* | The protocol of the port forwarding rule (e.g. TCP, UDP)
`instanceId`<br/>*UUID* | The id of the [instance](#instances) of the port forwarding rule
`instanceName`<br/>*string* | The name of the [instance](#instances) of the port forwarding rule
`networkId`<br/>*UUID* | The id of the [tier](#tiers) of the port forwarding rule
`vpcId`<br/>*UUID* | The id of the [VPC](#vpcs) of the port forwarding rule
`privateIp`<br/>*string* | The private IP address of the instance where requests will be forwarded
`privateIpId`<br/>*UUID* | The id of private IP address of the instance where requests will be forwarded
