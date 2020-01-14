---
weight: 404
title: Affinity groups
---

## Affinity groups

Affinity groups are a way of influencing on which host an [instance](#instances) will be deployed. An anti-affinity group (the only type of affinity group we support) allows you to put [instances](#instances) on different hosts to increase fault-tolerance. In the unlikely event of a host failure, your services would still be up on another host (assuming you distribute your services on multiple instances).

### List affinity groups

```shell
curl -X GET \
   -H "MC-Api-Key: your_api_key" \
"https://api.cloud.ca/v1/services/compute-on/test_area/affinitygroups"

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

<span class="method">GET</span> <code>/services/<a href="#service-connections">:service_code</a>/<a href="#environments">:environment_name</a>/affinitygroups</code>

Retrieve a list of all affinity groups in an [environment](#environments)

Attributes | Type | Description
---------- | ---- | ------------
`id` | *UUID* | The id of the affinity group
`name` | *string* | The name of the affinity group
`type` | *string* | The type of affinity group. We only support anti-affinity
`instanceIds` | *Array[UUID]* | The ids of the [instances](#instances) in the affinity group

### Retrieve an affinity group

```shell
curl -X GET \
   -H "MC-Api-Key: your_api_key" \
   "https://api.cloud.ca/v1/services/compute-on/test_area/affinitygroups/d4fd794f-66e1-4906-a720-d0afb04bd517"

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

<span class="method">GET</span> <code>/services/<a href="#service-connections">:service_code</a>/<a href="#environments">:environment_name</a>/affinitygroups/:id</code>

Retrieve information about an affinity group.

Attributes | Type | Description
---------- | ---- | ------------
`id` | *UUID* | The id of the affinity group
`name` | *string* | The name of the affinity group
`type` | *string* | The type of affinity group. We only support anti-affinity
`instanceIds` | *Array[UUID]* | The ids of the [instances](#instances) in the affinity group

### Create an affinity group

```shell
curl -X POST \
   -H "Content-Type: application/json" \
   -H "MC-Api-Key: your_api_key" \
   -d "request_body" \
   "https://api.cloud.ca/v1/services/compute-on/test_area/affinitygroups"

# Request should look like this
```

```json
{
   "name": "gnr",
   "description": "My affinity group",
   "type": "host anti-affinity",
   "instanceIds": [
     "92b4df86-fee3-4610-8167-78332b86362f"
   ]
}
```

<span class="method">POST</span> <code>/services/<a href="#service-connections">:service_code</a>/<a href="#environments">:environment_name</a>/affinitygroups</code>

Create an affinity group and add [instances](#instances) to it.

Required | Type | Description
-------- | ---- | ------------
`name` | *string* | The name of the new affinity group
`description` | *string* | A description of the affinity group
`type` | *string* | The type of new affinity group. We only support anti-affinity
`instanceIds` | *Array[UUID]* | The ids of the [instances](#instances) in the affinity group

### Update an affinity group

```shell
curl -X PUT \
   -H "Content-Type: application/json" \
   -H "MC-Api-Key: your_api_key" \
   -d "request_body" \
   "https://api.cloud.ca/v1/services/compute-on/test_area/affinitygroups/d4fd794f-66e1-4906-a720-d0afb04bd517"

# Request should look like this
```

```json
{
   "instanceIds": [
     "92b4df86-fee3-4610-8167-78332b86362f",
     "105f8b5e-5482-4bf5-88ca-7d7b7f431e3e"
   ]
}
```

<span class="method">PUT</span> <code>/services/<a href="#service-connections">:service_code</a>/<a href="#environments">:environment_name</a>/affinitygroups/:id</code>

Update the list of [instances](#instances) in the affinity group.

Required | Type | Description
-------- | ---- | ------------
`name` | *string* | The name of the new affinity group
`description` | *string* | A description of the affinity group
`type` | *string* | The type of new affinity group. We only support anti-affinity
`instanceIds` | *Array[UUID]* | The ids of the [instances](#instances) in the affinity group

### Delete an affinity group

```shell
curl -X DELETE \
   -H "MC-Api-Key: your_api_key" \
   "https://api.cloud.ca/v1/services/compute-on/test_area/affinitygroups/d4fd794f-66e1-4906-a720-d0afb04bd517"
```

<span class="method">DELETE</span> <code>/services/<a href="#service-connections">:service_code</a>/<a href="#environments">:environment_name</a>/affinitygroups/:id</code>

Delete an existing affinity group.
