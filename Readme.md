# Scalabe Jenkins on Kubernetes cluster

Scalable Jenkins installed on top of a Kubernetes cluster sandbox created using Minikube.

## Kubernetes sandbox: Installing kubectl and Minikube

Steps from the official Kubernetes documentation: https://kubernetes.io/docs/tasks/tools/install-minikube/

### Install a Hypervisor

Install Virtualbox or KVM.

If you choose Virtualbox, just follow the steps from Virtualbox site: https://www.virtualbox.org/wiki/Linux_Downloads

For KVM, in a Debian based system, you have just to install some packages:

```
$ sudo apt install qemu-kvm virtinst virt-top virt-manager seabios qemu-utils ovmf
```
And add your user to libvirt group:
```
$ sudo usermod -a -G libvirt you_user
```

### Install kubectl

If you use Ubuntu, you can simply istall kubectl using the snap package:

```
$ sudo snap install kubectl --classic
```

We are going to install it using apt instead:

```
$ sudo apt update && sudo apt install -y apt-transport-https
$ curl -s https://packages.cloud.google.com/apt/doc/apt-key.gpg | sudo apt-key add -
$ sudo touch /etc/apt/sources.list.d/kubernetes.list 
$ echo "deb http://apt.kubernetes.io/ kubernetes-xenial main" | sudo tee -a /etc/apt/sources.list.d/kubernetes.list
$ sudo apt update
$ sudo apt install -y kubectl
```

After installing, test to ensure the version is sufficiently up-to-date:

```
$ kubectl version
```

### Install Minikube

To install Minikube we follow the steps from: https://github.com/kubernetes/minikube/releases

We simply download the binary and copy it to /usr/local/bin.

```
$ curl -Lo minikube https://storage.googleapis.com/minikube/releases/v0.29.0/minikube-linux-amd64 && chmod +x minikube && sudo cp minikube /usr/local/bin/ && rm minikube
```

Usage: https://github.com/kubernetes/minikube/blob/v0.29.0/README.md

### Starting Kubernetes sandbox

Just run `minikube start` to download the Minikube ISO file, create the VM and start it.

## Jenkins master

To install the Jenkins master we are going to build a customized image, based on official image [jenkins/jenkins](https://hub.docker.com/r/jenkins/jenkins/). On top of which we are going to install all the needed plugins and extras.



## Jenkins slaves

