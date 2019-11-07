---
weight: 510
title: Site-to-site VPN
---

## Site-to-site VPN

A site-to-site VPN allows multiple sites to establish a secure connection over the public network. In our case, we are talking about a secure connection between your VPC and another network (e.g. VPC, offices).

<!-------------------- LIST SITE-TO-SITE VPNS -------------------->

### List site-to-site VPNs

```shell
curl -X GET \
   -H "MC-Api-Key: your_api_key" \
   "https://api.cloud.ca/v1/services/compute-on/test_area/sitetositevpns"

# Example:
```
```json
{
  "data": [
    {
        "id": "d49b2922-0581-4587-94df-6fe719327d0f",
        "name": "stargate",
        "state": "Connected",
        "vpcId": "3fe7d82a-f4c4-4552-ac3b-787fdafed4e7",
        "gateway":"19.19.19.19",
        "cidr":"10.12.0.2/22",
        "ipSecPsk": "WtOBS9GRux2XtJPtHY2TUvrv",
        "ikeEncryptionAlgorithm": "3des",
        "ikeHashAlgorithm": "sha1",
        "ikeDhGroup":"modp1536",
        "ikeLifetime":86400,
        "espEncryptionAlgorithm":"3des",
        "espHashAlgorithm":"sha1",
        "espPerfectForwardSecrecy":"modp1536",
        "espLifetime":3600,
        "dpd": false,
        "forceEncap": false
    }
  ],
  "metadata": {
    "recordCount": 1
  }
}
```

<span class="method">GET</span> <code>/services/<a href="#service-connections">:service_code</a>/<a href="#environments">:environment_name</a>/sitetositevpns</code>

Retrieve a list of all site-to-site VPNs in an [environment](#environments)

Attributes | Type | Description
-------------- | ---- | ------------
`id` | *UUID* | The id of the site-to-site VPN
`name` | *string* | The name of the site-to-site VPN
`state` | *string* | The state of the site-to-site VPN. Can be Connected, Pending, Disconnected or Error. If disconnected, you can try to use the [reset](#reset-the-connection-of-a-site-to-site-vpn) operation
`vpcId` | *UUID* | The VPC for which the site-to-site VPN was created.
`gateway` | *string*  | The gateway of the network you want to connect to. NOTE: you cannot use a gateway that has already been used by a site-to-site VPN in your environment
`cidr` | *string*  | CIDR of the network you want to connect to.
`ipSecPsk` | *string*  | IPSec pre-shared key. Must contain at least 10 alphanumeric characters.
`ikeEncryptionAlgorithm` | *string*  | The Internet Key Exchange (IKE) policy for phase-1. The supported encryption algorithms are AES128, AES192, AES256, and 3DES.
`ikeHashAlgorithm` | *string*  | The IKE hash for phase-1. The supported hash algorithms are SHA1 and MD5.
`ikeDhGroup` | *string*  | A public-key cryptography protocol which allows two parties to establish a shared secret over an insecure communications channel. The supported options are None, Group-5 (1536-bit) and Group-2 (1024-bit).
`ikeLifetime` | *integer*  | The phase-1 lifetime of the security association in seconds.
`espEncryptionAlgorithm` | *string*  | Encapsulating Security Payload (ESP) algorithm within phase-2. The supported encryption algorithms are AES128, AES192, AES256, and 3DES.
`espHashAlgorithm` | *string*  | Encapsulating Security Payload (ESP) hash for phase-2. Supported hash algorithms are SHA1 and MD5.
`espPerfectForwardSecrecy` | *string*  | Perfect Forward Secrecy (or PFS) is the property that ensures that a session key derived from a set of long-term public and private keys will not be compromised. The supported options are None, Group-5 (1536-bit) and Group-2 (1024-bit).
`espLifetime` | *integer*  | The phase-2 lifetime of the security association in seconds
`dpd` | *boolean*    | A method to detect an unavailable Internet Key Exchange (IKE) peer. 
`forceEncap` | *boolean* | Force encapsulation for NAT Traversal

Query Parameters | &nbsp;
-------------- | ---- | ------------
`vpc_id` | *UUID* | Filter the list to only retrieve the site-to-site VPNs of a [VPC](#vpcs)

<!-------------------- RETRIEVE A SITE-TO-SITE VPN -------------------->

### Retrieve a site-to-site VPN

```shell
curl -X GET \
   -H "MC-Api-Key: your_api_key" \
   "https://api.cloud.ca/v1/services/compute-on/test_area/sitetositevpns/d49b2922-0581-4587-94df-6fe719327d0f"

# Example:
```
```json
{
  "data": {
      "id": "d49b2922-0581-4587-94df-6fe719327d0f",
      "name": "stargate",
      "state": "Connected",
      "vpcId": "3fe7d82a-f4c4-4552-ac3b-787fdafed4e7",
      "gateway":"19.19.19.19",
      "cidr":"10.12.0.2/22",
      "ipSecPsk": "WtOBS9GRux2XtJPtHY2TUvrv",
      "ikeEncryptionAlgorithm": "3des",
      "ikeHashAlgorithm": "sha1",
      "ikeDhGroup":"modp1536",
      "ikeLifetime":86400,
      "espEncryptionAlgorithm":"3des",
      "espHashAlgorithm":"sha1",
      "espPerfectForwardSecrecy":"modp1536",
      "espLifetime":3600,
      "dpd": false,
      "forceEncap": false
  }
}
```

<span class="method">GET</span> <code>/services/<a href="#service-connections">:service_code</a>/<a href="#environments">:environment_name</a>/sitetositevpns/:id</code>

Retrieve information about a site-to-site VPN.

Attributes | Type | Description
-------------- | ---- | ------------
`id` | *UUID* | The id of the site-to-site VPN
`name` | *string* | The name of the site-to-site VPN
`state` | *string* | The state of the site-to-site VPN. Can be Connected, Pending, Disconnected or Error. If disconnected, you can try to use the [reset](#reset-the-connection-of-a-site-to-site-vpn) operation
`vpcId` | *UUID* | The VPC for which the site-to-site VPN was created.
`gateway` | *string*  | The gateway of the network you want to connect to. NOTE: you cannot use a gateway that has already been used by a site-to-site VPN in your environment
`cidr` | *string*  | CIDR of the network you want to connect to.
`ipSecPsk` | *string*  | IPSec pre-shared key. Must contain at least 10 alphanumeric characters.
`ikeEncryptionAlgorithm` | *string*  | The Internet Key Exchange (IKE) policy for phase-1. The supported encryption algorithms are AES128, AES192, AES256, and 3DES.
`ikeHashAlgorithm` | *string*  | The IKE hash for phase-1. The supported hash algorithms are SHA1 and MD5.
`ikeDhGroup` | *string*  | A public-key cryptography protocol which allows two parties to establish a shared secret over an insecure communications channel. The supported options are None, Group-5 (1536-bit) and Group-2 (1024-bit).
`ikeLifetime` | *integer*  | The phase-1 lifetime of the security association in seconds.
`espEncryptionAlgorithm` | *string*  | Encapsulating Security Payload (ESP) algorithm within phase-2. The supported encryption algorithms are AES128, AES192, AES256, and 3DES.
`espHashAlgorithm` | *string*  | Encapsulating Security Payload (ESP) hash for phase-2. Supported hash algorithms are SHA1 and MD5.
`espPerfectForwardSecrecy` | *string*  |  Perfect Forward Secrecy (or PFS) is the property that ensures that a session key derived from a set of long-term public and private keys will not be compromised. The supported options are None, Group-5 (1536-bit) and Group-2 (1024-bit).
`espLifetime` | *integer*  | The phase-2 lifetime of the security association in seconds
`dpd` | *boolean*    | A method to detect an unavailable Internet Key Exchange (IKE) peer. 
`forceEncap` | *boolean* | Force encapsulation for NAT Traversal

<!-------------------- CREATE A SITE-TO-SITE VPN -------------------->

### Create a site-to-site VPN

```shell

# Here is the absolute minimum information required to create a new site-to-site VPN:

curl -X POST \
   -H "Content-Type: application/json" \
   -H "MC-Api-Key: your_api_key" \
   -d "request_body" \
   "https://api.cloud.ca/v1/services/compute-on/test_area/sitetositevpns"

# Request should look like this
```
```json
{
      "name": "stargate",
      "vpcId": "3fe7d82a-f4c4-4552-ac3b-787fdafed4e7",
      "gateway":"19.19.19.19",
      "cidr":"10.12.0.2/22",
      "ipSecPsk": "WtOBS9GRux2XtJPtHY2TUvrv",
      "ikeEncryptionAlgorithm": "3des",
      "ikeHashAlgorithm": "sha1",
      "ikeDhGroup":"modp1536",
      "ikeLifetime":86400,
      "espEncryptionAlgorithm":"3des",
      "espHashAlgorithm":"sha1",
      "espPerfectForwardSecrecy":"modp1536",
      "espLifetime":3600,
      "dpd": false,
      "forceEncap": false
  }
```
 <span class="method">POST</span> <code>/services/<a href="#service-connections">:service_code</a>/<a href="#environments">:environment_name</a>/sitetositevpns</code>

Create a site-to-site VPN

Required | Type | Description
------------ | ---- | -----------
`name` | *string* | The name of the site-to-site VPN. Must be unique in the environment.
`vpcId` | *UUID* | The VPC for which the site-to-site VPN was created.
`gateway` | *string*  | The gateway of the network you want to connect to. NOTE: you cannot use a gateway that has already been used by a site-to-site VPN in your environment
`cidr` | *string*  | CIDR of the network you want to connect to.
`ipSecPsk` | *string*  | IPSec pre-shared key. Must contain at least 10 alphanumeric characters.
`ikeEncryptionAlgorithm` | *string*  | The Internet Key Exchange (IKE) policy for phase-1. The supported encryption algorithms are AES128, AES192, AES256, and 3DES.
`ikeHashAlgorithm` | *string*  | The IKE hash for phase-1. The supported hash algorithms are SHA1 and MD5.
`ikeLifetime` | *integer*  | The phase-1 lifetime of the security association in seconds.
`espEncryptionAlgorithm` | *string*  | Encapsulating Security Payload (ESP) algorithm within phase-2. The supported encryption algorithms are AES128, AES192, AES256, and 3DES.
`espHashAlgorithm` | *string*  | Encapsulating Security Payload (ESP) hash for phase-2. Supported hash algorithms are SHA1 and MD5.
`espLifetime` | *integer*  | The phase-2 lifetime of the security association in seconds

Optional | Type | Description
------------ | ---- | -----------
`ikeDhGroup` | *string*  | A public-key cryptography protocol which allows two parties to establish a shared secret over an insecure communications channel. The supported options are Group-5 (1536-bit) and Group-2 (1024-bit).
`espPerfectForwardSecrecy` | *string*  |  Perfect Forward Secrecy (or PFS) is the property that ensures that a session key derived from a set of long-term public and private keys will not be compromised. The supported options are Group-5 (1536-bit) and Group-2 (1024-bit).
`dpd` | *boolean*    | A method to detect an unavailable Internet Key Exchange (IKE) peer. Defaults to false
`forceEncap` | *boolean* | Force encapsulation for NAT Traversal. Defaults to false

<!-------------------- DELETE A SITE-TO-SITE VPN -------------------->


### Delete a site-to-site VPN


```shell

# Example:

curl -X DELETE \
   -H "MC-Api-Key: your_api_key" \
   "https://api.cloud.ca/v1/services/compute-on/test_area/sitetositevpns/d49b2922-0581-4587-94df-6fe719327d0f"
```

<span class="method">DELETE</span> <code>/services/<a href="#service-connections">:service_code</a>/<a href="#environments">:environment_name</a>/sitetositevpns/:id</code>

Delete an existing site-to-site VPN.


<!-------------------- RESET A SITE-TO-SITE VPN -------------------->

### Reset the connection of a site-to-site VPN

```shell

curl -X POST \
   -H "Content-Type: application/json" \
   -H "MC-Api-Key: your_api_key" \
   "https://api.cloud.ca/v1/services/compute-on/test_area/sitetositevpns/ca86b14f-20db-463d-b58a-9d3fa5959af2?operation=reset"

```
 <span class="method">POST</span> <code>/services/<a href="#service-connections">:service_code</a>/<a href="#environments">:environment_name</a>/sitetositevpns/:id?operation=reset</code>

Reset a site-to-site VPN.
