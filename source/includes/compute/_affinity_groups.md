### Affinity groups

Affinity groups are a way of influencing on which host an instance will be deployed. An anti-affinity group (the only type of affinity group we support) allows you to put instances on different hosts to increase fault-tolerance. In the unlikely event of a host failure, your services would still be up on another host (assuming you distribute your services on multiple instances).

<!-------------------- LIST AFFINITY GROUPS -------------------->

#### List affinity groups

```shell
curl -X GET -H "MC-Api-Key: [your-api-key]"
"https://api.cloud.ca/v1/services/compute-qc/demo-env/affinitygroups"

# Example:
```
```json
{
  "data": [{
    "id": "d4fd794f-66e1-4906-a720-d0afb04bd517",
    "name": "gnr",
    "type":"host anti-affinity",
    "instanceIds": [
      "92b4df86-fee3-4610-8167-78332b86362f"
    ]
  }],
  "metadata": {
    "recordCount": 1
  }
}
```

<code>GET https://api.cloud.ca/v1/services/<a href="#service-connections">:service_code</a>/<a href="#environments">:environment_name</a>/affinitygroups</code>

Retrieve a list of all affinity groups in an environment.

Attributes | &nbsp;
---------- | -----
id<br/>*UUID* | The id of the affinity group
name<br/>*string* | The name of the affinity group
type<br/>*string* | The type of affinity group. We only support anti-affinity
instanceIds<br/>*Array[UUID]* | The ids of the instances in the affinity group

#### Retrieve an affinity group

```shell
curl -X GET -H "MC-Api-Key: [your-api-key]"
"https://api.cloud.ca/v1/services/compute-qc/demo-env/affinitygroups/d4fd794f-66e1-4906-a720-d0afb04bd517"

# Example:
```
```json
{
  "data": {
    "id": "d4fd794f-66e1-4906-a720-d0afb04bd517",
    "name": "gnr",
    "type": "host anti-affinity",
    "instanceIds": [
      "92b4df86-fee3-4610-8167-78332b86362f"
    ]
  }
}
```

<code>GET https://api.cloud.ca/v1/services/<a href="#service-connections">:service_code</a>/<a href="#environments">:environment_name</a>/affinitygroups/:id</code>

Retrieve information about an affinity group.

Attributes | &nbsp;
---------- | -----
id<br/>*UUID* | The id of the affinity group
name<br/>*string* | The name of the affinity group
type<br/>*string* | The type of affinity group. We only support anti-affinity
instanceIds<br/>*Array[UUID]* | The ids of the instances in the affinity group
