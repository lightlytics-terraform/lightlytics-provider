## The StreamSecurity Terraform Provider



The StreamSecurity Terraform provider is used to connect your cloud account to StreamSec and integrate with various available features.

In order to use this provider, you must have an active account with [StreamSecurity](https://www.Stream.Security).

You can [start trial](https://app.streamsec.io/signup) or check out our [plans](https://www.stream.security/plans) and [contact us](https://www.stream.security/contact-us) or [book a demo](https://www.stream.security/book-demo).


## Requirements
- A StreamSec account
- Credentials to StreamSec platform (Email & Password)


## Building the provider
1. Clone the [terraform-provider-lightlytics](https://github.com/lightlytics-terraform/terraform-provider-lightlytics) repository
2. Navigate to the provider directory
3. Install the provider by running the following command:
```
make install
```


## Usage
```hcl
# Configure Lightlytics provider host and credentials

terraform {
  required_providers {
    lightlytics  = {
      version    = "0.3"
      source     = "lightlytics.com/api/lightlytics"
    }
  }
}

provider "lightlytics" {
  host           = "<https://<env_name>.streamsec.io>"
  username       = "<Your_StreamSec_Login_Email>"
  password       = "<Your_StreamSec_Login_Password>"
  workspace_id   = "<Your_StreamSec_Workspace_ID>"  ## Can be obtained from StreamSec platform, if not specified, it will use the first WS
}

# Configure AWS account

resource "lightlytics_account" "aws" {
  account_type     = "AWS"
  cloud_account_id = "<Your_Cloud_Provider_Account_ID>"
  display_name     = "<Your_Desired_StreamSec_Integration_Display_Name>"
  stack_region     = "us-east-1"
  cloud_regions    = ["us-east-1", "us-east-2"]
}

resource "lightlytics_kubernetes_account" "k8s" {
  display_name   = "<Your_Desired_StreamSec_Kubernetes_Integration_Display_Name>"
  eks_arn   = "<Your_EKS_ARN>"
}
```


## Inputs
| Variable Name    | Description                                                                | Notes                                               | Type           | Required? | Default |
|:-----------------| :------------------------------------------------------------------------- | :-------------------------------------------------- |:---------------|:--------- |:--------|
| host             | Your environment URL including https://                                    | e.g `https://org.streamsec.io`                   | `string`       | Yes       | n/a     |
| username         | Your StreamSec user Email                                                |                                                     | `string`       | Yes       | n/a     |
| password         | Your StreamSec user password                                             |                                                     | `string`       | Yes       | n/a     |
| workspace_id     | Can be obtained from StreamSec platform                                  | Will use default workspace in case not specified    | `string`       | No        | n/a     |
| cloud_account_id | Your cloud provider account ID                                             |                       			                   | `string`       | Yes       | n/a     |
| display_name     | Your integration display name within StreamSec platform                  |                                                     | `string`       | No       | n/a     |
| stack_region     | The primary region where StreamSec read access resources will be created |                                                     | `string`       | Yes       | n/a     |
| cloud_regions      | List of desired regions to be scanned                                      | us-east-1 region is mandatory for the integration   | `list(string)` | Yes       | n/a     | 



Documentation
-------------
If you're new to StreamSecurity and want to get started, feel free to [contact us](https://www.stream.security/contact-us) or checkout our [documentation](https://docs.streamsec.io) website.


Community
---------
- Join StreamSecurity community on [Slack](https://join.slack.com/t/lightlyticscommunity/shared_invite/zt-1f7dk2yo7-xBTOU_o4tOnAjoFxfHVF8Q)


Getting Help
------------
Please use these resources for getting help:
- [Slack](https://join.slack.com/t/lightlyticscommunity/shared_invite/zt-1f7dk2yo7-xBTOU_o4tOnAjoFxfHVF8Q)
- Email: support@stream.security
