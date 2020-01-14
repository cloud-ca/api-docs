---
weight: 503
title: Network ACLs
---

## Network ACLs

Manage access control lists and their rules. To apply an ACL to a network, [replace the ACL of a network](#replace-the-network-acl-of-a-network).

### List network ACLs

```shell
curl -X GET \
   -H "MC-Api-Key: your_api_key" \
   "https://api.cloud.ca/v1/services/compute-on/test_area/networkacls?vpc_id=eb763d03-9935-4cd4-8a42-99134e242ccb"
```
```json
{
  "data": [
    {
      "id": "736d0c2e-d6b5-43fc-bcf0-732fce9a509e",
      "vpcId": "eb763d03-9935-4cd4-8a42-99134e242ccb",
      "name": "custom-1",
      "description": "Allows network egress"
    },
    {
      "id": "3246de94-e7e7-11e3-9187-06669c0000ad",
      "name": "default_allow",
      "description": "Default Network ACL Allow All"
    },
    {
      "id": "32467792-e7e7-11e3-9187-06669c0000ad",
      "name": "default_deny",
      "description": "Default Network ACL Deny All"
    }
  ],
  "metadata": {
    "recordCount": 3
  }
}
```
```go
resources, _ := ccaClient.GetResources("compute-on", "test_area")
ccaResources := resources.(cloudca.Resources)
acls, err := ccaResources.NetworkAcls.ListByVpcId("eb763d03-9935-4cd4-8a42-99134e242ccb")
```
<span class="method">GET</span> <code>/services/<a href="#service-connections">:service_code</a>/<a href="#environments">:environment_name</a>/networkacls?vpc_id=:vpc_id</code>

Retrieve a list of network ACLs in a VPC.

Attributes | Type | Description
---------- | ---- | -----------
`id` | *UUID*            | The id of the network ACL
`name` | *string*        | The name of the network ACL
`description` | *string* | The description of the network ACL
`vpcId` | *UUID*         | The VPC where this rule is available. Not present on `default_allow` and `default_deny` ACLs


Query Parameters | Type | Description
---------------- | ---- | -----------
`vpc_id` | *UUID*    | Filter the list to only retrieve the network ACLs of a specific [VPC](#vpcs)

### Retrieve a network ACL

```shell
curl -X GET \
   -H "MC-Api-Key: your_api_key" \
   "https://api.cloud.ca/v1/services/compute-on/test_area/networkacls/:id"
```
```json
{
  "data": {
    "id": "736d0c2e-d6b5-43fc-bcf0-732fce9a509e",
    "vpcId": "eb763d03-9935-4cd4-8a42-99134e242ccb",
    "name": "custom-1",
    "description": "Allows network egress"
  }
}
```
```go
resources, _ := ccaClient.GetResources("compute-on", "test_area")
ccaResources := resources.(cloudca.Resources)
acl, err := ccaResources.NetworkAcls.Get("736d0c2e-d6b5-43fc-bcf0-732fce9a509e")
```
<span class="method">GET</span> <code>/services/<a href="#service-connections">:service_code</a>/<a href="#environments">:environment_name</a>/networkacls/:id</code>

Retrieve a specific network ACL by its id.

Attributes | Type | Description
---------- | ---- | -----------
`id` | *UUID*            | The id of the network ACL
`name` | *string*        | The name of the network ACL
`description` | *string* | The description of the network ACL
`vpcId` | *UUID*         | The VPC where this rule is available. Not present on `default_allow` and `default_deny` ACLs

### Create network ACL

```shell
curl -X POST \
   -H "Content-Type: application/json" \
   -H "MC-Api-Key: your_api_key" \
   -d "request_body" \
   "https://api.cloud.ca/v1/services/compute-on/test_area/networkacls"
```
```go
resources, _ := ccaClient.GetResources("compute-on", "test_area")
ccaResources := resources.(cloudca.Resources)
acl, err := ccaResources.NetworkAcls.Create(cloudca.NetworkAcl{
  Name: "network-ingress",
  Description: "Allows network ingress",
  VpcId: "eb763d03-9935-4cd4-8a42-99134e242ccb",
})
```
```dart
resource "cloudca_network_acl" "my_acl" {
  service_code = "compute-on"
  environment_name = "test_area"
  name = "network-ingress"
  description = "Allows network ingress"
  vpc_id = "eb763d03-9935-4cd4-8a42-99134e242ccb"
}
```
<span class="method">POST</span> <code>/services/<a href="#service-connections">:service_code</a>/<a href="#environments">:environment_name</a>/networkacls</code>

Create a new network ACL associated to a VPC.

Required | Type | Description
-------- | ---- | -----------
`name` | *string*        | The name of the network ACL
`description` | *string* | The description of the network ACL
`vpcId` | *UUID*         | Networks of this VPC will be able to use the new ACL

### Delete a network ACL

```shell
curl -X DELETE \
   -H "MC-Api-Key: your_api_key" \
   "https://api.cloud.ca/v1/services/compute-on/test_area/networkacls/736d0c2e-d6b5-43fc-bcf0-732fce9a509e"
```
```go
resources, _ := ccaClient.GetResources("compute-on", "test_area")
ccaResources := resources.(cloudca.Resources)
success, err := ccaResources.NetworkAcls.Delete("736d0c2e-d6b5-43fc-bcf0-732fce9a509e")
```
<span class="method">DELETE</span> <code>/services/<a href="#service-connections">:service_code</a>/<a href="#environments">:environment_name</a>/networkacls/:id</code>

Delete an ACL and all of its rules.

<!-- ACL rules -->
### List a network ACL's rules

```shell
curl -X GET \
   -H "MC-Api-Key: your_api_key" \
   "https://api.cloud.ca/v1/services/compute-on/test_area/networkaclrules?network_acl_id=3246de94-e7e7-11e3-9187-06669c0000ad"
```
```json
{
  "data": [
    {
      "id": "3247167a-e7e7-11e3-9187-06669c0000ad",
      "networkAclId": "3246de94-e7e7-11e3-9187-06669c0000ad",
      "ruleNumber": "2",
      "cidr": "0.0.0.0/0",
      "action": "Allow",
      "protocol": "ALL",
      "trafficType": "Egress",
      "state": "Active"
    },
    {
      "id": "3246fdb6-e7e7-11e3-9187-06669c0000ad",
      "networkAclId": "3246de94-e7e7-11e3-9187-06669c0000ad",
      "ruleNumber": "1",
      "cidr": "0.0.0.0/0",
      "action": "Allow",
      "protocol": "ALL",
      "trafficType": "Ingress",
      "state": "Active"
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
rules, err := ccaResources.NetworkAclRules.ListByNetworkAclId("3246de94-e7e7-11e3-9187-06669c0000ad")
```
<span class="method">GET</span> <code>/services/<a href="#service-connections">:service_code</a>/<a href="#environments">:environment_name</a>/networkaclrules?network_acl_id=:network_acl_id</code>

List a network ACL's rules.

Attributes | Type | Description
---------- | ---- | -----------
`id` | *UUID*            | The id of the network ACL rule
`networkAclId` | *UUID*  | The id of the network ACL that this rule belongs to
`ruleNumber` | *int* | The relative position of this rule in its ACL
`cidr` | *CIDR*          | The network addresses targeted by this rule
`action` | *string*      | What to do with traffic matched by this rule. Either Allow or Deny
`protocol` | *string*    | The protocols targeted by this rule. TCP, UDP, ICMP, or ALL
`trafficType` | *string* | The direction of traffic targeted by this rule. Either Ingress or Egress
`state` | *string*       | The state of this rule. Either Active or Inactive

Query Parameters | Type | Description
---------------- | ---- | -----------
`network_acl_id` | *UUID* | Filter the list to only retrieve the rules of a specific [network ACL](#network-acls)

### Retrieve a network ACL rule

```shell
curl -X GET \
   -H "MC-Api-Key: your_api_key" \
   "https://api.cloud.ca/v1/services/compute-on/test_area/networkaclrules/3247167a-e7e7-11e3-9187-06669c0000ad"
```
```json
{
  "data": {
    "id": "3247167a-e7e7-11e3-9187-06669c0000ad",
    "networkAclId": "3246de94-e7e7-11e3-9187-06669c0000ad",
    "ruleNumber": "2",
    "cidr": "0.0.0.0/0",
    "action": "Allow",
    "protocol": "ALL",
    "trafficType": "Egress",
    "state": "Active"
  }
}
```
```go
resources, _ := ccaClient.GetResources("compute-on", "test_area")
ccaResources := resources.(cloudca.Resources)
rules, err := ccaResources.NetworkAclRules.Get("3247167a-e7e7-11e3-9187-06669c0000ad")
```
<span class="method">GET</span> <code>/services/<a href="#service-connections">:service_code</a>/<a href="#environments">:environment_name</a>/networkaclrules/:id</code>

Attributes | Type | Description
---------- | ---- | -----------
`id` | *UUID*            | The id of the network ACL rule
`networkAclId` | *UUID*  | The id of the network ACL that this rule belongs to
`ruleNumber` | *int* | The relative position of this rule in its ACL
`cidr` | *CIDR*          | The network addresses targeted by this rule
`action` | *string*      | What to do with traffic matched by this rule. Either Allow or Deny
`protocol` | *string*    | The protocols targeted by this rule. TCP, UDP, ICMP, or ALL
`trafficType` | *string* | The direction of traffic targeted by this rule. Either Ingress or Egress
`state` | *string*       | The state of this rule. Either Active or Inactive

### Create a network ACL rule

```shell
curl -X POST \
   -H "Content-Type: application/json" \
   -H "MC-Api-Key: your_api_key" \
   -d "request_body" \
   "https://api.cloud.ca/v1/services/compute-on/test_area/networkaclrules"
```
```go
resources, _ := ccaClient.GetResources("compute-on", "test_area")
ccaResources := resources.(cloudca.Resources)
rule, err := ccaResources.NetworkAclRules.Create(cloudca.NetworkAclRule{
  NetworkAclId: "3247167a-e7e7-11e3-9187-06669c0000ad",
  RuleNumber: 1,
  Cidr: "0.0.0.0/0",
  Action: "Deny",
  TrafficType: "Ingress",
  Protocol: "ALL",
})
```
```dart
resource "cloudca_network_acl_rule" "my_acl_rule" {
  service_code = "compute-on"
  environment_name = "test_area"
  network_acl_id = "3247167a-e7e7-11e3-9187-06669c0000ad"
  rule_number = 1
  cidr = "0.0.0.0/0"
  action = "Deny"
  traffic_type = "Ingress"
  protocol = "ALL"
}
```
<span class="method">POST</span> <code>/services/<a href="#service-connections">:service_code</a>/<a href="#environments">:environment_name</a>/networkaclrules</code>

Required | Type | Description
-------- | ---- | -----------
`networkAclId` | *UUID*  | The id of the network ACL to add this rule to
`ruleNumber` | *int* | The relative position of this rule in its ACL
`cidr` | *CIDR*          | The network addresses targeted by this rule
`action` | *string*      | What to do with traffic matched by this rule. Either Allow or Deny
`protocol` | *string*    | The protocols targeted by this rule. TCP, UDP, ICMP, or ALL
`trafficType` | *string* | The direction of traffic targeted by this rule. Either Ingress or Egress

<aside class="notice">
For rules with protocol <code>ALL</code>, no protocol-specific information is required. For all other protocols, see the protocol-specific fields below.
</aside>

Protocol-specific | Type | Description
----------------- | ---- | -----------
`startPort` | *int* | The start of the port range targeted by this rule. Required if the protocol is TCP or UDP
`endPort` | *int*   | The end of the port range targeted by this rule. Required if the protocol is TCP or UDP
`icmpType` | *int*  | ICMP message type. Required if the protocol is ICMP
`icmpCode` | *int*  | ICMP message error code. Required if the protocol is ICMP

### Update a network ACL rule

```shell
curl -X PUT \
   -H "Content-Type: application/json" \
   -H "MC-Api-Key: your_api_key" \
   -d "request_body" \
   "https://api.cloud.ca/v1/services/compute-on/test_area/networkaclrules/3247167a-e7e7-11e3-9187-06669c0000ad"
```
```go
resources, _ := ccaClient.GetResources("compute-on", "test_area")
ccaResources := resources.(cloudca.Resources)
rule, err := ccaResources.NetworkAclRules.Update("3247167a-e7e7-11e3-9187-06669c0000ad", cloudca.NetworkAclRule{
  RuleNumber: 3,
  Action: "Allow",
})
```
<span class="method">PUT</span> <code>/services/<a href="#service-connections">:service_code</a>/<a href="#environments">:environment_name</a>/networkaclrules/:id</code>

Update a network ACL rule.

<aside class="notice">
A rule's protocol can only be changed from TCP to UDP or vice versa.
</aside>

Optional | Type | Description
-------- | ---- | -----------
`ruleNumber` | *int* | The relative position of this rule in its ACL
`cidr` | *CIDR*          | The network addresses targeted by this rule
`action` | *string*      | What to do with traffic matched by this rule. Either Allow or Deny
`protocol` | *string*    | The protocols targeted by this rule. TCP, UDP, ICMP, or ALL
`trafficType` | *string* | The direction of traffic targeted by this rule. Either Ingress or Egress
`startPort` | *int*  | The start of the port range targeted by this rule
`endPort` | *int*    | The end of the port range targeted by this rule
`icmpType` | *int*   | ICMP message type
`icmpCode` | *int*   | ICMP message error code

### Delete a network ACL rule

```shell
curl -X DELETE \
   -H "MC-Api-Key: your_api_key" \
   "https://api.cloud.ca/v1/services/compute-on/test_area/networkaclrules/3247167a-e7e7-11e3-9187-06669c0000ad"
```
```go
resources, _ := ccaClient.GetResources("compute-on", "test_area")
ccaResources := resources.(cloudca.Resources)
success, err := ccaResources.NetworkAclRules.Delete("3247167a-e7e7-11e3-9187-06669c0000ad")
```
<span class="method">DELETE</span> <code>/services/<a href="#service-connections">:service_code</a>/<a href="#environments">:environment_name</a>/networkaclrules/:id</code>

Delete a specific rule of a network ACL.
