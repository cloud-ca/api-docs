### Templates

#### List templates

```shell
curl -X GET -H "MC-Api-Key: [your-api-key]"
"https://api.cloud.ca/v1/services/compute-qc/demo-env/templates"

# Example:
```
```json
{
  "data": [{
    "id": "0b3fea04-b1ed-48cf-921d-96795dfe9a81",
    "name": "ubuntu",
    "description": "Example template",
    "size": 52428800,
    "isPublic": false,
    "isReady": true,
    "isDynamicallyScalable": true,
    "sshKeyEnabled": true,
    "created":"2016-10-24 2:40:29 PM EDT",
    "osType": "Other (64-bit)",
    "osTypeId": "1 b3ee00c-e7e7-11e3-9187-06669c0000ad",
    "hypevisor": "XenServer",
    "format": "VHD"
  }],
  "metadata": {
    "recordCount": 1
  }
}
```

Attributes | &nbsp;
---------- | -----
id<br/>*UUID* | The id of the template
name<br/>*string* | The name of the template
description<br/>*string* | The description of the template
size<br/>*long* | The size of the template in bytes
isPublic<br/>*boolean* | ...
isReady<br/>*boolean* | ...
isDynamicallyScalable<br/>*boolean* | ...
created<br/>*string* | The creation date of the template
osType<br/>*string* | ...
osTypeId<br/>*string* | ...
hypervisor<br/>*string* | ...
format<br/>*string* | ...

#### Retrieve a template

```shell
curl -X GET -H "MC-Api-Key: [your-api-key]"
"https://api.cloud.ca/v1/services/compute-qc/demo-env/templates/162cdfcb-45e5-4aa6-81c4-124c94621bdb"

# Example:
```
```json
{
  "data": {
    "id": "0b3fea04-b1ed-48cf-921d-96795dfe9a81",
    "name": "ubuntu",
    "description": "Example template",
    "size": 52428800,
    "isPublic": false,
    "isReady": true,
    "isDynamicallyScalable": true,
    "sshKeyEnabled": true,
    "created":"2016-10-24 2:40:29 PM EDT",
    "osType": "Other (64-bit)",
    "osTypeId": "1 b3ee00c-e7e7-11e3-9187-06669c0000ad",
    "hypevisor": "XenServer",
    "format": "VHD"
  }
}
```
