### Volumes


<!-------------------- LIST VOLUMES -------------------->

#### List volumes

```shell
curl -X GET -H "MC-Api-Key: [your-api-key]"
"https://api.cloud.ca/v1/services/compute-qc/demo-env/volumes"

# Example:
```
```json
{
  "data": [
    {
      "id": "1bd672f4-b274-4371-a792-b0a6c6778cc7",
      "name": "DOUGLAS-ADM",
      "type": "os",
      "creationDate": "2016-10-19T14:25:41-0400",
      "instanceId": "b6145e8b-abd3-456c-832c-f3db86a6acfe",
      "instanceName": "i-douglas-ADM",
      "zoneId": "2c62ab1e-eef9-4aa3-8626-faf37d65c5ea",
      "zoneName": "dev1_zone1",
      "state": "Ready",
      "sizeInGb": 40
    }
  ],
  "metadata": {
    "recordCount": 1
  }
}
```

<code>GET https://api.cloud.ca/v1/services/<a href="#service-connections">:service_code</a>/<a href="#environments">:environment_name</a>/volumes</code>

Retrieve a list of all volumes in an environment.

Attributes | &nbsp;
---------- | -----
id<br/>*UUID* | The id of the volume
name<br/>*string* | The name of the volume
type<br/>*string* | The type of the volume. `os` if it is a root volume of an instance, `data` otherwise
creationDate<br/>*string* | The creation date of the volume
instanceId<br/>*UUID* | The id of the instance to which the volume is attached
instanceName<br/>*string* | The name of the instance to which the volume is attached
zoneId<br/>*UUID* | The id of the zone where the volume was created
zoneName<br/>*string* | The name of the zone where the volume was created
state<br/>*string* | The state of the volume
sizeInGb<br/>*int* | The size in gigabytes of the volume

<!-- iops<br/>*int* | The number of IOPS of the volume -->

<!-------------------- RETRIEVE A VOLUME -------------------->

#### Retrieve a volume

```shell
curl -X GET -H "MC-Api-Key: [your-api-key]"
"https://api.cloud.ca/v1/services/compute-qc/demo-env/volumes/1bd672f4-b274-4371-a792-b0a6c6778cc7"

# Example:
```
```json
{
  "data": {
    "id": "1bd672f4-b274-4371-a792-b0a6c6778cc7",
    "name": "deep_thought_42",
    "type": "data",
    "creationDate": "2016-10-19T14:25:41-0400",
    "instanceId": "b6145e8b-abd3-456c-832c-f3db86a6acfe",
    "instanceName": "i-douglas-ADM",
    "zoneId": "2c62ab1e-eef9-4aa3-8626-faf37d65c5ea",
    "zoneName": "dev1_zone1",
    "diskOfferingId": "fb446518-5777-4221-8845-8cb9eeb9dc80",
    "diskOfferingName": "40 GB - Intermediate",
    "state": "Ready",
    "sizeInGb": 40
  }
}
```

<code>GET https://api.cloud.ca/v1/services/<a href="#service-connections">:service_code</a>/<a href="#environments">:environment_name</a>/volumes/:id</code>

Retrieve information about an volume.

Attributes | &nbsp;
---------- | -----
id<br/>*UUID* | The id of the volume
name<br/>*string* | The name of the volume
type<br/>*string* | The type of the volume. `os` if it is a root volume of an instance, `data` otherwise
creationDate<br/>*string* | The creation date of the volume
instanceId<br/>*UUID* | The id of the instance to which the volume is attached
instanceName<br/>*string* | The name of the instance to which the volume is attached
zoneId<br/>*UUID* | The id of the zone where the volume was created
zoneName<br/>*string* | The name of the zone where the volume was created
state<br/>*string* | The state of the volume
sizeInGb<br/>*int* | The size in gigabytes of the volume

<!-- iops<br/>*int* | The number of IOPS of the volume -->


<!-------------------- CREATE VOLUMES -------------------->

#### Create a volume

```shell
curl -X POST -H "Content-Type: application/json" -H "MC-Api-Key: [your-api-key]" -d "{
  \"name\": \"\",
  \"diskOfferingId\": \"166f85eb-b4a2-4000-8e0c-24104d551f60\",
  \"zoneId\": \"37c0d1f2-523a-4c43-a522-26932992b193\",
  \"instanceId\": \"c043e651-8b3f-4941-b47f-5ecb77f3423b\",
}" "https://api.cloud.ca/v1/services/compute-qc/testing/volumes"

# Request should look like this
```
```json
{
   "name": "",
   "diskOfferingId": "166f85eb-b4a2-4000-8e0c-24104d551f60",
   "zoneId": "37c0d1f2-523a-4c43-a522-26932992b193",
   "instanceId": "c043e651-8b3f-4941-b47f-5ecb77f3423b"
}
```

<code>POST https://api.cloud.ca/v1/services/<a href="#service-connections">:service_code</a>/<a href="#environments">:environment_name</a>/volumes</code>

Create a volume in an environment. Also, by specifying an instance, it will attach the new volume to it.

Required | &nbsp;
---------- | -----
name<br/>*string* | The name of the new volume
diskOfferingId<br/>*UUID* | The disk offering to use for the volume
zoneId<br/>*UUID* | The id of the zone where the volume will be created

Optional | &nbsp;
---------- | -----
instanceId<br/>*UUID* | The id of the instance to which the created volume should be attached
