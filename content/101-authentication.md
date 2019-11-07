---
weight: 101
title: Authentication
---

## Authentication

```go
import "github.com/cloud-ca/go-cloudca"
ccaClient := cca.NewCcaClient("your_api_key")
```

```terraform
provider "cloudca" {
  api_key = "${var.my_api_key}"
}
```

```shell
## To authenticate, add a header
## Make sure to replace `your_api_key` with your API key.
curl "https://api.cloud.ca/v1/organizations" \
   -H "MC-Api-Key: your_api_key"
```

API endpoints are secured by the same role-based access control (RBAC) as the cloud.ca portal. To identify who is making the requests, it is required to add a header to your HTTP requests:

`MC-Api-Key: your_api_key`

<aside class="notice">
You must replace <code>your_api_key</code> with your personal API key.
</aside>

The API key is found from the API keys section under the user profile menu. If you don't see cloud.ca API keys section, contact your system administrator as you may not have the permission to see that section. **Your API key carries the same privileges as your cloud.ca account, so be sure to keep it secret**. If you think your API has been compromised, regenerate your API key from the API keys section.
