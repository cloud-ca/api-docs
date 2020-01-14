---
weight: 800
title: Zones
---

# Zones

Each zone consists of physically isolated hosts, storage, and networking infrastructure. Like deploying workloads across regions, deploying workloads over multiple zones can help ensure high availability of applications.

### List zones

```shell
curl -X GET \
   -H "MC-Api-Key: your_api_key" \
   "https://api.cloud.ca/v1/services/compute-on/test_area/zones"

# The above command returns JSON structured like this:
```
```json
{
    "data": [
        {
            "id": "ea901007-056b-4c50-bb3a-2dd635fce2ab",
            "name": "ON-1"
        }
    ],
    "metadata": {
        "recordCount": 1
    }
}
```
```go
resources, _ := ccaClient.GetResources("compute-on", "test_area")
ccaResources := resources.(cloudca.Resources)
zones, _ := ccaResources.Zones.List()
```

<span class="method">GET</span> <code>/services/<a href="#service-connections">:service_code</a>/<a href="#environments">:environment_name</a>/zones</code>

Retrieve a list of available zones.

Attributes | Type | Description
-------------- | ---- | ------------
`id` | *UUID* | The id of the zone
`name` | *string* | The name of the zone

### Retrieve a zone

```shell
curl -X GET \
   -H "MC-Api-Key: your_api_key" \
   "https://api.cloud.ca/v1/services/compute-on/test_area/zones/ea901007-056b-4c50-bb3a-2dd635fce2ab"

# The above command returns JSON structured like this:
```
```json
{
    "data": {
        "id": "ea901007-056b-4c50-bb3a-2dd635fce2ab",
        "name": "ON-1"
    }
}

```
```go
resources, _ := ccaClient.GetResources("compute-on", "test_area")
ccaResources := resources.(cloudca.Resources)
zones, _ := ccaResources.Zones.Get("ea901007-056b-4c50-bb3a-2dd635fce2ab")
```

<span class="method">GET</span> <code>/services/<a href="#service-connections">:service_code</a>/<a href="#environments">:environment_name</a>/zones/:id</code>

Retrieve a zone

Attributes | Type | Description
-------------- | ---- | ------------
`id` | *UUID* | The id of the zone
`name` | *string* | The name of the zone
