---
weight: 403
title: SSH keys
---

## SSH keys

SSH keys can be assigned to default users of instances by using the [associate SSH key](#associate-an-ssh-key-to-an-instance) operation.

### List SSH keys

```shell
curl -X GET \
   -H "MC-Api-Key: your_api_key" \
   "https://api.cloud.ca/v1/services/compute-on/test_area/sshkeys"

# Example:
```

```json
{
  "data": [{
    "name": "mellon",
    "fingerprint": "91:8d:71:ca:2d:2c:ad:97:26:db:cb:c3:df:9a:e9:b6"
  }],
  "metadata": {
    "recordCount": 1
  }
}
```

<span class="method">GET</span> <code>/services/<a href="#service-connections">:service_code</a>/<a href="#environments">:environment_name</a>/sshkeys</code>

Retrieve a list of all SSH keys in an [environment](#environments)

Attributes | Type | Description
---------- | ---- | ------------
`name` | *string* | The name of the SSH key
`fingerprint` | *string* | A short sequence of bytes used to identify the SSH key.

### Retrieve an SSH key

```shell
curl -X GET \
   -H "MC-Api-Key: your_api_key" \
   "https://api.cloud.ca/v1/services/compute-on/test_area/sshkeys/mellon"

# Example:
```

```json
{
  "data": {
    "name": "mellon",
    "fingerprint": "91:8d:71:ca:2d:2c:ad:97:26:db:cb:c3:df:9a:e9:b6"
  }
}
```

<span class="method">GET</span> <code>/services/<a href="#service-connections">:service_code</a>/<a href="#environments">:environment_name</a>/sshkeys/:name</code>

Retrieve information about an SSH key of an [environment](#environments)

Attributes | Type | Description
---------- | ---- | ------------
`name` | *string* | The name of the SSH key
`fingerprint` | *string* | A short sequence of bytes used to identify the SSH key.
