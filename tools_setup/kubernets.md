https://www.linuxtechi.com/how-to-install-minikube-on-ubuntu/

Commands:

sudo apt update
sudo apt upgrade
sudo reboot
sudo apt install docker.io
sudo usermod -aG docker ubuntu

sudo apt install -y curl wget apt-transport-https
curl -LO https://storage.googleapis.com/minikube/releases/latest/minikube-linux-amd64
sudo install minikube-linux-amd64 /usr/local/bin/minikube
minikube version
curl -LO https://storage.googleapis.com/kubernetes-release/release/`curl -s https://storage.googleapis.com/kubernetes-release/release/stable.txt`/bin/linux/amd64/kubectl
chmod +x kubectl
sudo mv kubectl /usr/local/bin/
sudo usermod -aG docker $USER && newgrp docker

minikube start --driver=docker

kubectl create namespace backstage




Step 1) Apply updates
Apply all updates of existing packages of your system by executing the following apt commands,

$ sudo apt update -y
$ sudo apt upgrade -y
Once all the updates are installed then reboot your system once.

$ sudo reboot
Step 2) Install Minikube dependencies
Install the following minikube dependencies by running beneath command,

$ sudo apt install -y curl wget apt-transport-https
Step 3) Download Minikube Binary
Use the following curl command to download latest minikube binary,

$ curl -LO https://storage.googleapis.com/minikube/releases/latest/minikube-linux-amd64
Once the binary is downloaded, copy it to the path /usr/local/bin and set the executable permissions on it

$ sudo install minikube-linux-amd64 /usr/local/bin/minikube
Verify the minikube version

$ minikube version
minikube version: v1.30.1
commit: 08896fd1dc362c097c925146c4a0d0dac715ace0
$
Note: At the time of writing this tutorial, latest version of minikube was v1.30.1.

Step 4) Install Kubectl utility
Kubectl is a command line utility which is used to interact with Kubernetes cluster. It is used for managing deployments, service and pods etc. Use below curl command to download latest version of kubectl.

$ curl -LO https://storage.googleapis.com/kubernetes-release/release/`curl -s https://storage.googleapis.com/kubernetes-release/release/stable.txt`/bin/linux/amd64/kubectl
Once kubectl is downloaded then set the executable permissions on kubectl binary and move it to the path /usr/local/bin.

$ chmod +x kubectl
$ sudo mv kubectl /usr/local/bin/
Now verify the kubectl version

$ kubectl version -o yaml
kubectl-version-check-minikube-ubuntu

Step 5) Start minikube
As we are already stated in the beginning that we would be using docker as base for minikue, so start the minikube with the docker driver, run

$ minikube start --driver=docker
In case you want to start minikube with customize resources and want installer to automatically select the driver then you can run following command,

$ minikube start --addons=ingress --cpus=2 --cni=flannel --install-addons=true --kubernetes-version=stable --memory=6g
Output would like below,

minikube-start-driver-docker-ubuntu

Perfect, above confirms that minikube cluster has been configured and started successfully.

Run below minikube command to check status,

pkumar@linuxtechi:~$ minikube status
minikube
type: Control Plane
host: Running
kubelet: Running
apiserver: Running
kubeconfig: Configured
pkumar@linuxtechi:~$
Run following kubectl command to verify the Kubernetes version, node status and cluster info.

$ kubectl cluster-info
$ kubectl get nodes
Output of above commands would like below:

Kubectl-cluster-info-minikube-Ubuntu

Step 6) Managing Addons on minikube
By default, only couple of addons are enabled during minikube installation, to see the addons of minikube, run the below command.

$ minikube addons list
Minikube-addons-Ubuntu-22-04

If you wish to enable any addons run the below minikube command,

$ minikube addons enable <addon-name>

Let’s assume we want to enable and access kubernetes dashboard , run

$ minikube dashboard
It will open the Kubernetes dashboard in the web browser.

Minikube-Dashboard-Ubuntu-22-04

Kubernetes-Dashboard-Ubuntu

To enable Ingress controller addon, run

$ minikube addons enable ingress
Enable-Ingress-Addon-Minikube-Ubuntu

Step 7) Verify Minikube Installation
To verify the minikube installation, let’s try to deploy nginx based deployment.

Run below kubectl command to install nginx based deployment.

$ kubectl create deployment my-nginx --image=nginx
Run following kubectl command to verify deployment status

$ kubectl get deployments.apps my-nginx
$ kubectl get pods
Output of above commands would look like below:

Nginx-based-deployment-k8s

Expose the deployment using following command,

$ kubectl expose deployment my-nginx --name=my-nginx-svc --type=NodePort --port=80
$ kubectl get svc my-nginx-svc
Use below command to get your service url,

$ minikube service my-nginx-svc --url
http://192.168.49.2:31895
$
Now try to access your nginx based deployment using above url,

$ curl http://192.168.49.2:31895
Output,

Curl-nginx-deployment-testing

Great, above confirms that NGINX application is accessible.

Step 8) Managing Minikube Cluster
To stop the minikube, run

$ minikube stop
To delete the minikube, run

$ minikube delete
To Start the minikube, run

$ minikube start
In case you want to start the minikube with higher resource like 8 GB RM and 4 CPU then execute following commands one after the another.

$ minikube config set cpus 4
$ minikube config set memory 8192
$ minikube delete
$ minikube start
That’s all from this tutorial, I hope you have learned how to install Minikube on Ubuntu 22.04 & 22.04. Please don’t hesitate to share your feedback and comments.

Also Read: How to Configure Static IP Address on Ubuntu 22.04 LTS