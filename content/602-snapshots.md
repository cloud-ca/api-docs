---
weight: 602
title: Snapshots
---

## Snapshots

 A volume snapshot is a full image of a volume. They are often considered as backups, but in reality this is not 100% true since you have only the data written on disk. Volume Snapshots are typically used to derive new templates out of a running instance.

<!-------------------- LIST SNAPSHOTS -------------------->

### List snapshots

```shell
curl -X GET \
   -H "MC-Api-Key: your_api_key" \
   "https://api.cloud.ca/v1/services/compute-on/test_area/snapshots"

# Example:
```
```json
{
  "data": [
    {
      "id": "33a27b8d-5a27-42a5-aec4-37606e372bda",
      "name": "i-douglas-ADM_foo_20161116211009",
      "state": "BackedUp",
      "intervalType": "MANUAL",
      "volumeId": "c779ca42-6966-41af-a7dc-23db4e41d4ee",
      "volume": "ROOT-35545",
      "volumeType": "ROOT-35545"
    }
  ],
  "metadata": {
    "recordCount": 1
  }
}
```

<span class="method">GET</span> <code>/services/<a href="#service-connections">:service_code</a>/<a href="#environments">:environment_name</a>/snapshots</code>

Retrieve a list of all snapshots in an [environment](#environments)

Attributes | Type | Description
-------------- | ---- | ------------
`id` | *UUID* | The id of the snapshot
`name` | *string* | The name of the snapshot
`state` | *string* | The state of the snapshot
`intervalType` | *string* | The interval type. `MANUAL` means that you created the snapshot manually (i.e. it's not a recurring snapshot)
`volumeId` | *UUID* | The id of the [volume](#volumes) that was snapshotted
`volume` | *string* | The name of the [volume](#volumes) that was snapshotted
`volumeType` | *string* | The type of the [volume](#volumes) that was snapshotted

Query Parameters | &nbsp;
-------------- | ---- | ------------
`volume_id` | *UUID* | Filter the list to only retrieve the snapshots of a specific [volume](#volumes)

<!-------------------- RETRIEVE A SNAPSHOT -------------------->

### Retrieve a snapshot

```shell
curl -X GET \
   -H "MC-Api-Key: your_api_key" \
   "https://api.cloud.ca/v1/services/compute-on/test_area/snapshots/1bd672f4-b274-4371-a792-b0a6c6778cc7"

# Example:
```
```json
{
  "data": {
    "id": "33a27b8d-5a27-42a5-aec4-37606e372bda",
    "name": "i-douglas-ADM_foo_20161116211009",
    "state": "BackedUp",
    "intervalType": "MANUAL",
    "volumeId": "c779ca42-6966-41af-a7dc-23db4e41d4ee",
    "volume": "ROOT-35545",
    "volumeType": "ROOT-35545"
  }
}
```

<span class="method">GET</span> <code>/services/<a href="#service-connections">:service_code</a>/<a href="#environments">:environment_name</a>/snapshots/:id</code>

Retrieve information about a snapshot.

Attributes | Type | Description
-------------- | ---- | ------------
`id` | *UUID* | The id of the snapshot
`name` | *string* | The name of the snapshot
`state` | *string* | The state of the snapshot
`intervalType` | *string* | The interval type. `MANUAL` means that you created the snapshot manually (i.e. it's not a recurring snapshot)
`volumeId` | *UUID* | The id of the [volume](#volumes) that was snapshotted
`volume` | *string* | The name of the [volume](#volumes) that was snapshotted
`volumeType` | *string* | The type of the [volume](#volumes) that was snapshotted
