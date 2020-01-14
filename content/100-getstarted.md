---
weight: 100
title: Getting started
---

# Getting started edited

The cloud.ca API allows you to manage your environments and provision resources in a simple programmatic way using standard HTTP requests.

The API is  [RESTful](https://en.wikipedia.org/wiki/Representational_state_transfer). Responses, successful or not, are returned in [JSON](http://www.json.org/). Request bodies must be [JSON](http://www.json.org/), and should be made over SSL.

API endpoint: `https://api.cloud.ca/v1`

We have also developed tools to help consume our APIs. If you use `go`, check out our [library](https://github.com/cloud-ca/go-cloudca). If you use Terraform, check out our [provider](https://github.com/cloud-ca/terraform-cloudca). NB: both are being actively developed, so there is still some functionality missing.
