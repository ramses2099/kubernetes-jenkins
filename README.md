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
```