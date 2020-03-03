# Setting up Kubernetes from Command Line
This section talks about the setup of Kubernetes from the Command Line once the AWS Console section is completed

## Set up for AWS communication
The AWS Command Line Interface (CLI) is a unified tool to manage the AWS services

### Install awscli
To install awscli use the pip3 command. Install in the _--user_ home directory
```
pip3 install --user awscli
```

### Create AWS credentials file
Create a file _~/.aws/credentials_ in the home directory with the following content for accessing IAM user and setting up default region
```
[default]
aws_access_key_id=###
aws_secret_access_key=###
region=us-east-1
output=json
```

### Test AWS Connection
To test the connection execute the _version_ command
```
aws --version
```

## Setup of eksctl
eksctl is a simple CLI tool for creating clusters on EKS

### Installation
Download the eksctl from github
```
curl --silent --location "https://github.com/weaveworks/eksctl/releases/download/latest_release/eksctl_$(uname -s)_amd64.tar.gz" | tar xz -C /tmp

sudo mv /tmp/eksctl /usr/local/bin
```

### Test
To test the installation of eksctl execute the _version_ command
```
eksctl version
```


## Setup of kubectl
Kubectl is a command line tool for controlling Kubernetes clusters

### Installation
Kubectl is located in https location. To download from https location, install the _apt-transport-https_. Once downloaded, install kubectl
```
sudo apt-get install -y apt-transport-https
curl -s https://packages.cloud.google.com/apt/doc/apt-key.gpg | sudo apt-key add -
echo "deb https://apt.kubernetes.io/ kubernetes-xenial main" | sudo tee -a /etc/apt/sources.list.d/kubernetes.list
sudo apt-get update
sudo apt-get install -y kubectl
```

### Test
To test the installation of kubectl execute the _version_ command
```
kubectl version --short --client
```
