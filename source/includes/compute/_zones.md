## Zones

Each zone consists of physically isolated hosts, storage, and networking infrastructure. Like deploying workloads across regions, deploying workloads over multiple zones can help ensure high availability of applications. NB: the ontario region (i.e. compute-on) has a single zone, but the quebec region (i.e. compute-qc) has two.

#### List zones

```shell
curl -X GET -H "MC-Api-Key: [your-api-key]"
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

<code>GET https://api.cloud.ca/v1/services/<a href="#service-connections">:service_code</a>/<a href="#environments">:environment_name</a>/zones</code>

Retrieve a list of available zones.

Attributes | &nbsp;
---------- | -----
id<br/>*UUID* | ---
name<br/>*string* | ---

#### Retrieve a zone

```shell
curl -X GET -H "MC-Api-Key: [your-api-key]"
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

<code>GET https://api.cloud.ca/v1/services/<a href="#service-connections">:service_code</a>/<a href="#environments">:environment_name</a>/zones/:id</code>

Retrieve a zone

Attributes | &nbsp;
---------- | -----
id<br/>*UUID* | ---
name<br/>*string* | ---
