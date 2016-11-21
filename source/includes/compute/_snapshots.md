### Snapshots


<!-------------------- LIST SNAPSHOTS -------------------->

#### List snapshots

```shell
curl -X GET -H "MC-Api-Key: [your-api-key]"
"https://api.cloud.ca/v1/services/compute-qc/demo-env/snapshots"

# Example:
```
```json
{
  "data": [
    {
      "id": "",
      "name": ""
    }
  ],
  "metadata": {
    "recordCount": 1
  }
}
```

<code>GET https://api.cloud.ca/v1/services/<a href="#service-connections">:service_code</a>/<a href="#environments">:environment_name</a>/snapshots</code>

Retrieve a list of all snapshots in an environment.

Attributes | &nbsp;
---------- | -----
id<br/>*UUID* | The id of the snapshot
name<br/>*string* | The name of the snapshot


<!-------------------- RETRIEVE A SNAPSHOT -------------------->

#### Retrieve a snapshot

```shell
curl -X GET -H "MC-Api-Key: [your-api-key]"
"https://api.cloud.ca/v1/services/compute-qc/demo-env/snapshots/1bd672f4-b274-4371-a792-b0a6c6778cc7"

# Example:
```
```json
{
  "data": {
    "id": "",
    "name": "",
  }
}
```

<code>GET https://api.cloud.ca/v1/services/<a href="#service-connections">:service_code</a>/<a href="#environments">:environment_name</a>/snapshots/:id</code>

Retrieve information about a snapshot.

Attributes | &nbsp;
---------- | -----
id<br/>*UUID* | The id of the snapshot
name<br/>*string* | The name of the snapshot
