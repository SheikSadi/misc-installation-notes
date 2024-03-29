# Misc Installation Notes
> Notes on installing software I struggled with, then found solution.

## 1. `gcloud` | `ubuntu` (22.04.3 LTS)
###i. Problem: `Unable to locate package google-cloud-cli`
> Motivation: I struggled with installing `gcloud` by following [the official guide](https://cloud.google.com/sdk/docs/install). It was  complaining the above problem. I found an answer to resolve this at [StackOverFlow](https://stackoverflow.com/questions/23247943/trouble-installing-google-cloud-sdk-in-ubuntu)
### Solution
> Credits: [@Samantha](https://stackoverflow.com/users/3359481/samantha)
```sh
curl https://dl.google.com/dl/cloudsdk/release/install_google_cloud_sdk.bash | bash
```
Find the backup for the above link here: [install_google_cloud_sdk.bash](/resources/install_google_cloud_sdk.bash)

## 2. `docker` | `ubuntu` (22.04.3 LTS, 20.04.6 LTS)
### i. Problem with Installation: `docker-desktop : Depends: docker-ce-cli but it is not installable`
> Motivation: I struggled with installing `docker-destop` by following [the official guide](https://docs.docker.com/desktop/install/ubuntu/). Here are the logs -
```sh
Reading package lists... Done
Building dependency tree       
Reading state information... Done
Note, selecting 'docker-desktop' instead of './docker-desktop-4.25.2-amd64.deb'
Some packages could not be installed. This may mean that you have
requested an impossible situation or if you are using the unstable
distribution that some required packages have not yet been created
or been moved out of Incoming.
The following information may help to resolve the situation:

The following packages have unmet dependencies:
docker-desktop : Depends: docker-ce-cli but it is not installable
```
### Solution for 20.04.6 LTS
- First you need to install `docker-ce-cli` and for that you have to first add the repository keyring to your local machine  
```sh
# download the keyring
curl -fsSL https://download.docker.com/linux/ubuntu/gpg | sudo gpg --dearmor -o /usr/share/keyrings/docker-archive-keyring.gpg
# add the keyring to /etc/apt/...
echo "deb [arch=$(dpkg --print-architecture) signed-by=/usr/share/keyrings/docker-archive-keyring.gpg] https://download.docker.com/linux/ubuntu $(lsb_release -cs) stable" | sudo tee /etc/apt/sources.list.d/docker.list > /dev/null
# now it will install
sudo apt-get install docker-ce-cli
```
- After that you can follow as the offical instuction:

### Solution for 22.04.3 LTS
- First you need to install `docker-ce-cli` and for that you have to first add the repository keyring to your local machine  
```sh
# add the Docker PPA repository to your system:
sudo add-apt-repository universe
sudo add-apt-repository ppa:docker/stable
sudo apt update
sudo apt install docker-ce-cli
```
### ii. Problem with LOGIN
> Motivation
```
Error saving credentials: error storing credentials - err: exit status 1, out: `error storing credentials - err: exit status 1, out: `pass not initialized: exit status 1: Error: password store is empty. Try "pass init".``
```
### Solution
After installing docker-desktop, you must initialize a gpg key and initialize it to be able to successfully login with `docker login` command.
```
$ gpg --gen-key
```
The above command will guide you through some steps and finally show an output. Take note of the pub key. It's needed in the next step. You can find the key anytime with `gpg --list-keys`. You will be asked to set up a passphrase for verification. Note it down somewhere safe.
```
$ pass init <your-gpg-key>
```
Now you can `docker login` without problem

## 3. `google-chrome` | `ubuntu`
### i. Could not get lock /var/lib/dpkg/lock-frontend
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
