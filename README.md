# kubernetes-jenkins
Deploy jenkins in kubernetes k8

# step 1 - create namespace
```
kubectl create namespace devops-tools
```

# step 2 - run manifest jenkins.serviceAccount.yml
```
kubectl apply -f jenkins.serviceAccount.yaml
```

# step 3 - run manifest jenkins.volume.yml
```
kubectl get nodes
--mportant Note: Replace 'worker-node01' with any one of your cluster worker nodes hostname.

kubectl create -f jenkins.volume.yaml
```
# step 4 - run manifest jenkins.deployment.yml
```
runAsUser=1000
fsGroup=1000   # Or custom ID, per above
mkdir -p /var/jenkins_home
chown -R $runAsUser:$fsGroup /var/jenkins_home
chmod -R g+rwX /var/jenkins_home
```
```
kubectl apply -f jenkins.deployment.yml
```
# check the deployment status
```
kubectl get deployments -n devops-tools
```
# for more details
```
kubectl describe deployments --namespace=devops-tools
```
# step 5 - run manifest jenkins.service.yml
```
kubectl apply -f jenkins.service.yml
```
# step 6 - port service publish 32500
```
http://<node-ip>:32500
```
# step 7 - get the master password of jenkins
```
kubectl get pods --namespace=devops-tools
```

# step 8 - the password in the log of the pod
```
kubectl logs jenkins-f5b474494-87vvb --namespace=devops-tools
```