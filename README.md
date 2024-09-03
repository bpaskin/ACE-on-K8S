### App Connect Enterprise on Kubernetes without an Operator

1. Make sure you are logged onto your Kubernetes cluster and have a command line interface to run `kubectl` commands
2. (Optional) Create a new namespace.  `name` is the name of the new namespace to create
```
kubectl create namespace <name>
```
3. Switch to that namespace (`name` = name from step 2)
```
kubectl config set-context --current --namespace=<name>
```
4. Get your [entitlement key](https://myibm.ibm.com/products-services/containerlibrary) from IBM.  Must be entitled to the product.
5. Create a secret to be used a pull secret with the key
```
kubectl create secret docker-registry ibm-entitlement-key --docker-server=cp.icr.io --docker-username=cp --docker-password=<key from IBM registry>
```
6. Upload an App Connect Enterprise bar file as a `ConfigMap` (`name` is the name of the bar file)
```
kubectl create configmap ace-bar --from-file=<name>.bar
```
7. Update the `ace-deployment.yaml` with the proper namespace, image version, and bar file name
8. Deploy the deployment
```
kubectl apply -f ace-deployment.yaml
```



𐕣 Funeral Winter 𐕣
