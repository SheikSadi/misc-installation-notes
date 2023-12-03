# Misc Installation Notes
> Notes on installing software I struggled with, then found solution.

## `gcloud` | `ubuntu` (22.04.3 LTS)
### Problem: `Unable to locate package google-cloud-cli`
> Motivation: I struggled with installing `gcloud` by following [the official guide](https://cloud.google.com/sdk/docs/install). It was  complaining the above problem. I found an answer to resolve this at [StackOverFlow](https://stackoverflow.com/questions/23247943/trouble-installing-google-cloud-sdk-in-ubuntu)
### Solution
> Credits: [@Samantha](https://stackoverflow.com/users/3359481/samantha)
```sh
curl https://dl.google.com/dl/cloudsdk/release/install_google_cloud_sdk.bash | bash
```
Find the backup for the above link here: [install_google_cloud_sdk.bash](/resources/install_google_cloud_sdk.bash)

[TBC]
