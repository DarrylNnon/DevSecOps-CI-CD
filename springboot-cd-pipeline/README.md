PRODUCTION GRADE DEVSECOPS CICD Pipeline

Create 1 EC2 server


Minikube server with 4 GB storage - t2.medium


Setup Minikube

$ Install Docker
$ sudo apt update && sudo apt -y install docker.io

 Install kubectl
$ curl -LO https://storage.googleapis.com/kubernetes-release/release/v1.23.7/bin/linux/amd64/kubectl && chmod +x ./kubectl && sudo mv ./kubectl /usr/local/bin/kubectl

 Install Minikube
$ curl -Lo minikube https://storage.googleapis.com/minikube/releases/v1.23.2/minikube-linux-amd64 && chmod +x minikube && sudo mv minikube /usr/local/bin/

 Start Minikube
$  sudo apt install conntrack
$  minikube start --vm-driver=none



Setup ArgoCD

$ kubectl create namespace argocd
$ kubectl apply -n argocd -f https://raw.githubusercontent.com/argoproj/argo-cd/stable/manifests/install.yaml
$ kubectl patch svc argocd-server -n argocd -p '{"spec": {"type": "NodePort"}}' 

For version 1.9 or later:
$ kubectl -n argocd get secret argocd-initial-admin-secret -o jsonpath="{.data.password}" | base64 -d && echo
