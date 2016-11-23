### Public IP addresses

#### List public IPs

```shell
curl -X GET \
   -H "MC-Api-Key: your_api_key" \
   "https://api.cloud.ca/v1/services/compute-on/test_area/publicipaddresses"

# Example:
```
```json
{
   "data": [
      {
         "id": "0ed72307-e33d-4d41-90b7-7d2b4f0d1ae0",
         "instances": [
            {
               "id": "986cfea3-4a94-407d-b915-eb2d49e4323f",
               "name": "i-pdube-F49"
            }
         ],
         "ipAddress": "69.196.164.98",
         "networkId": "def89cb6-f897-435a-ad7f-6b2d05ab11e6",
         "networkName": "web",
         "purposes": [
            "PORT_FORWARDING"
         ],
         "state": "Allocated",
         "vpcId": "0687f5ce-89f9-47c8-9f58-c522455d56eb",
         "vpcName": "secondary",
         "zoneId": "ea901007-056b-4c50-bb3a-2dd635fce2ab",
         "zoneName": "ON-1"
      },
      {
         "id": "10001e7d-b4ef-489b-836e-0619a383bc8d",
         "ipAddress": "208.80.152.201",
         "purposes": [
            "SOURCE_NAT"
         ],
         "state": "Allocated",
         "vpcId": "0687f5ce-89f9-47c8-9f58-c522455d56eb",
         "vpcName": "primary",
         "zoneId": "ea901007-056b-4c50-bb3a-2dd635fce2ab",
         "zoneName": "ON-1"
      }
   ],
   "metadata": {
      "recordCount": 2
   }
}
```
```go
resources, _ := ccaClient.GetResources("compute-on", "test_area")
ccaResources := resources.(cloudca.Resources)
publicIps, _ := ccaResources.PublicIps.List()
```

<code>GET /services/<a href="#service-connections">:service_code</a>/<a href="#environments">:environment_name</a>/publicipaddresses</code>

List allocated public IP addresses.

Attributes | &nbsp;
---------- | -----
`id`<br/>*UUID* | The id of the public IP
`instances`<br/>*Array[[Instance](#instances)]* | The associated instances <br/>*includes*:`id`,`name`
`ipAddress`<br/>*string* | The IP address (e.g. 208.80.154.224)
`networkId`<br/>*UUID* | The network id
`networkName`<br/>*string* | The associated network name
`purposes`<br/>*Array[string]* | The list of purposes of the IP address. Possible values: STATIC_NAT, PORT_FORWARDING, LOAD_BALANCING, SOURCE_NAT or SOURCE_NAT and VPN
`state`<br/>*string* | The state
`vpcId`<br/>*UUID* | The VPC id
`vpcName`<br/>*string* | The VPC name
`zoneId`<br/>*UUID* | The zone id
`zoneName`<br/>*string* | The zone name

#### Retrieve a public IP

```shell
curl -X GET -H "MC-Api-Key: your_api_key"
"https://api.cloud.ca/v1/services/compute-on/test_area/publicipaddresses/10001e7d-b4ef-489b-836e-0619a383bc8d"

# Example:
```
```json
{
   "data": {
      "id": "10001e7d-b4ef-489b-836e-0619a383bc8d",
      "ipAddress": "208.80.152.201",
      "purposes": [
          "SOURCE_NAT"
      ],
      "state": "Allocated",
      "vpcId": "0687f5ce-89f9-47c8-9f58-c522455d56eb",
      "vpcName": "primary",
      "zoneId": "ea901007-056b-4c50-bb3a-2dd635fce2ab",
      "zoneName": "ON-1"
   }
}
```
```go
resources, _ := ccaClient.GetResources("compute-on", "test_area")
ccaResources := resources.(cloudca.Resources)
publicIp, _ := ccaResources.PublicIps.Get("10001e7d-b4ef-489b-836e-0619a383bc8d")
```

<code>GET /services/<a href="#service-connections">:service_code</a>/<a href="#environments">:environment_name</a>/publicipaddresses/:id</code>

Retrieve a public IP address.

Attributes | &nbsp;
---------- | -----
`id`<br/>*UUID* | The id of the public IP
`instances`<br/>*Array[[Instance](#instances)]* | The associated instances <br/>*includes*:`id`,`name`
`ipAddress`<br/>*string* | The IP address (e.g. 208.80.154.224)
`networkId`<br/>*UUID* | The network id
`networkName`<br/>*string* | The associated network name
`purposes`<br/>*Array[string]* | The list of purposes of the IP address. Possible values: STATIC_NAT, PORT_FORWARDING, LOAD_BALANCING, SOURCE_NAT or SOURCE_NAT and VPN
`state`<br/>*string* | The state
`vpcId`<br/>*UUID* | The VPC id
`vpcName`<br/>*string* | The VPC name
`zoneId`<br/>*UUID* | The zone id
`zoneName`<br/>*string* | The zone name

#### Acquire a public IP

```shell
curl -X POST \
   -H "MC-Api-Key: your_api_key" \
   -H "Content-Type: application/json" \
   -d "request_body" \
   "https://api.cloud.ca/v1/services/compute-on/test_area/publicipaddresses"

# Request should look like this
```
```json
{
   "vpcId": "0687f5ce-89f9-47c8-9f58-c522455d56eb"
}
```

<code>POST /services/<a href="#service-connections">:service_code</a>/<a href="#environments">:environment_name</a>/publicipaddresses</code>

Acquire a public IP address for a VPC.

Required | &nbsp;
---------- | -----
`vpcId`<br/>*UUID* | The VPC id


#### Release a public IP

```shell
curl -X DELETE \
   -H "MC-Api-Key: your_api_key" \
   "https://api.cloud.ca/v1/services/compute-on/test_area/publicipaddresses/a723b2b1-e343-4ea1-afe0-bf345a99a92b"
```

<code>DELETE /services/<a href="#service-connections">:service_code</a>/<a href="#environments">:environment_name</a>/publicipaddresses/:id</code>

Release a public IP. When acquiring a public IP, you are not guaranteed to receive a previously owned public IP, so be careful when releasing public IPs.

#### Enable static NAT

```shell
curl -X POST \
   -H "MC-Api-Key: your_api_key" \
   -H "Content-Type: application/json" \
   -d "request_body" \
   "https://api.cloud.ca/v1/services/compute-on/test_area/publicipaddresses/a723b2b1-e343-4ea1-afe0-bf345a99a92b?operation=enableStaticNat"

# Request should look like this
```
```json
{
   "privateIpId": "5e30609d-7098-4d93-8317-3ecfe316ed00"
}
```

<code>POST /services/<a href="#service-connections">:service_code</a>/<a href="#environments">:environment_name</a>/publicipaddresses/:id?operation=enableStaticNat</code>

Enable static NAT on a public IP address.

Required | &nbsp;
---------- | -----
`privateIpId`<br/>*string* | The private IP id of the instance which is to be available on that IP. It can also be done on a [secondary IP](#secondary-ip) id.

#### Disable static NAT

```shell
curl -X POST \
   -H "MC-Api-Key: your_api_key" \
   "https://api.cloud.ca/v1/services/compute-on/test_area/publicipaddresses/a723b2b1-e343-4ea1-afe0-bf345a99a92b?operation=disableStaticNat"

```

<code>POST /services/<a href="#service-connections">:service_code</a>/<a href="#environments">:environment_name</a>/publicipaddresses/:id?operation=disableStaticNat</code>

Disable static NAT on that public IP.
