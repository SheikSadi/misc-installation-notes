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

# `google-chrome` | `ubuntu`
### Could not get lock /var/lib/dpkg/lock-frontend
> After downloading the `google-chrome-stable_current_amd64.deb` file from the offical page, I tried `sudo apt install google-chrome-stable_current_amd64.deb` as usual. But, it didn't work and kept showing the following logs infinitely:
```sh
E: Could not get lock /var/lib/dpkg/lock-frontend - open (11: Resource temporarily unavailable)  
E: Unable to acquire the dpkg frontend lock (/var/lib/dpkg/lock-frontend), is another process using it?
```
### Solution
Instead of using `apt install`, you should use `dpkg` command as follows:
```sh
sudo dpkg -i google-chrome-stable_current_amd64.deb
# after installation
google-chrome
```

[TBC]
