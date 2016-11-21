### Tiers
#### Replace ACL

```shell
curl -X POST -H "Content-Type: application/json" -H "MC-Api-Key: [your-api-key]" -d "{
  \"networkAclId\": \"736d0c2e-d6b5-43fc-bcf0-732fce9a509e\"
}" "https://api.cloud.ca/v1/services/compute-on/test_area/tiers/f242547b-b6d9-4aa4-b6b1-6bdd66a36289?operation=replace"
```
```go
resources, _ := ccaClient.GetResources("compute-on", "test_area")
ccaResources := resources.(cloudca.Resources)
success, err := ccaResources.Tiers.ChangeAcl("f242547b-b6d9-4aa4-b6b1-6bdd66a36289", "736d0c2e-d6b5-43fc-bcf0-732fce9a509e")
```
<code>POST https://api.cloud.ca/v1/services/<a href="#service-connections">:service_code</a>/<a href="#environments">:environment_name</a>/tiers/:id?operation=replace</code>

Replace the network ACL of a tier.

Required                  | &nbsp;
--------------------------|-------
`networkAclId`<br/>*UUID* | A network ACL in the same VPC as this tier
