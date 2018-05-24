# spinnaker Installation


===> Install helm.

-> Download package
$ wget https://storage.googleapis.com/kubernetes-helm/helm-v2.9.1-linux-amd64.tar.gz

-> Untar

$ tar -zxvf helm-v2.0.0-linux-amd64.tgz

-> Move helm binary to executable path.

$ mv linux-amd64/helm /usr/local/bin/helm

$ export PATH=$PATH:/usr/local/bin (if helm help doesn't works)

-> Create a service account. (In case of permission denied error while running helm install command)

$ kubectl create serviceaccount tiller --namespace kube-system

$ kubectl create -f rbac-tiller.yaml

-> Initialize helm

$ helm init --service-account tiller

-> Download default config file - values.yaml for spinnaker installation.

$ wget https://github.com/kubernetes/charts/blob/master/stable/spinnaker/values.yaml

-> Install spinnaker helm chart.

$ helm install -n spinnaker stable/spinnaker -f values.yaml  --version 0.3.5 --namespace kube-system

TIP: Needs atleast 7.5 GB/2vCPUSs for scheduling pods.
     
     Delete helm chart (helm del --purge spinnaker) if it times out and then install again. 

