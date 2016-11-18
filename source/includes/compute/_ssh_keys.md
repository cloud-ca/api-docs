### SSH keys
SSH keys can be assigned to default users of instances by using the [associate SSH key](#associate-an-ssh-key-to-an-instance) operation.

<!-------------------- LIST SSH KEYS -------------------->

#### List SSH keys

```shell
curl -X GET -H "MC-Api-Key: [your-api-key]"
"https://api.cloud.ca/v1/services/compute-qc/demo-env/sshkeys"

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

<code>GET https://api.cloud.ca/v1/services/<a href="#service-connections">:service_code</a>/<a href="#environments">:environment_name</a>/sshkeys</code>

Retrieve a list of all SSH keys in an environment.

Attributes | &nbsp;
---------- | -----
name<br/>*string* | The name of the SSH key
fingerprint<br/>*string* | A short sequence of bytes used to identify the SSH key.


<!-------------------- RETRIEVE AN SSH KEY -------------------->


#### Retrieve an SSH key

```shell
curl -X GET -H "MC-Api-Key: [your-api-key]"
"https://api.cloud.ca/v1/services/compute-qc/demo-env/sshkeys/mellon"

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

<code>GET https://api.cloud.ca/v1/services/<a href="#service-connections">:service_code</a>/<a href="#environments">:environment_name</a>/sshkeys/:name</code>

Retrieve information about an SSH key of an environment.

Attributes | &nbsp;
---------- | -----
name<br/>*string* | The name of the SSH key
fingerprint<br/>*string* | A short sequence of bytes used to identify the SSH key.
