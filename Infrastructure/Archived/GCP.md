# GCP Hosting
The MC server was hosted on a N2D Compute Engine VM on Google Cloud Platform (GCP) during March 2020 and the beginning of April 2020.

We had switched to Vultr beginning April 9, 2020.

# VM instance information
The VM instance running on it was running Ubuntu 18.04 LTS. More information on the VM configuration and GCP will be added at a later time. 

# How to access the server

## Install GCP SDK for accessing the server
Follow this guide for debian and ubuntu based systems (More systems will be added later): https://cloud.google.com/sdk/docs/quickstart-debian-ubuntu

WARNING: gcloud (and the Google Cloud SDK) is proprietary (not open source) software. You can alternatively use
SSH in a terminal (which means you have to put keys into the "project metadata" which has security issues in larger
groups using the SSH permission) or https://github.com/googleapis/google-cloud-python

See: https://cloud.google.com/compute/docs/instances/connecting-advanced

Run the following commands in a terminal that you're fine with running proprietary software on:

## Add the Cloud SDK distribution URI as a package source
~~~
echo "deb [signed-by=/usr/share/keyrings/cloud.google.gpg] http://packages.cloud.google.com/apt cloud-sdk main" | sudo tee -a /etc/apt/sources.list.d/google-cloud-sdk.list
~~~
## Import the Google Cloud Platform public key
~~~
curl https://packages.cloud.google.com/apt/doc/apt-key.gpg | sudo apt-key --keyring /usr/share/keyrings/cloud.google.gpg add -
~~~

## Update the package list and install the Cloud SDK
~~~
sudo apt-get update && sudo apt-get install google-cloud-sdk
~~~
## Configure GCP
run:
~~~
gcloud config set project rhit-mc-server
~~~
then:
~~~
gcloud compute ssh root@vm-mc-server-node-n2d-ssd  --zone=us-central1-a
~~~
