# Kubernetes

`kubectl` talks to a cluster. Helm installs charts. minikube and kind each start a local cluster. k9s is a terminal UI on top of `kubectl`. The Docker daemon these local clusters use is in `linux/docker.md`.

```bash
$ sudo pacman -S kubectl helm minikube kind k9s
$ kubectl version --client
$ helm version
```

`kubectl` reads `~/.kube/config`. That file holds cluster credentials. Do not commit it.

## Local cluster

minikube runs a one-node cluster in Docker:

```bash
$ minikube start --driver=docker
$ minikube status
$ minikube ip
$ minikube stop
$ minikube delete
$ kubectl config current-context
$ kubectl config use-context minikube
```

`stop` shuts the cluster down and keeps it. `delete` removes it.

kind also runs Kubernetes in Docker. The context name is `kind-` plus the cluster name.

```bash
$ kind create cluster --name dev
$ kind get clusters
$ kind get kubeconfig --name dev
$ kubectl config use-context kind-dev
$ kind load docker-image <image> --name dev
$ kind delete cluster --name dev
```

`load docker-image` puts a local image into the kind nodes. A kind cluster cannot see images that only exist on the host until you load them.

Addons and the dashboard are minikube commands:

```bash
$ minikube addons list
$ minikube addons enable metrics-server
$ minikube dashboard
$ minikube service <name>
```

`metrics-server` is what `kubectl top` needs. `minikube service` opens the URL of a Service.

## Context and namespace

```bash
$ kubectl config get-contexts
$ kubectl config current-context
$ kubectl config use-context <context>
$ kubectl config view --minify
$ kubectl config set-context --current --namespace=<namespace>
$ kubectl get namespaces
$ kubectl create namespace <namespace>
$ kubectl delete namespace <namespace>
```

`--minify` prints only the current context. `set-context --current --namespace` makes later commands use that namespace, so you can omit `-n`.

Most commands take `-n <namespace>`. `get` also takes `-A` for every namespace.

```bash
$ kubectl get pods -n <namespace>
$ kubectl get pods -A
```

## Look

```bash
$ kubectl cluster-info
$ kubectl api-resources
$ kubectl explain pod
$ kubectl explain pod.spec.containers
$ kubectl get nodes
$ kubectl get pods
$ kubectl get pods -o wide
$ kubectl get deploy,svc,po
$ kubectl get all
$ kubectl get pod <name> -o yaml
$ kubectl describe pod <name>
$ kubectl describe node <name>
$ kubectl get events --sort-by=.lastTimestamp
```

Short names: `po` pods, `deploy` deployments, `svc` services, `sts` statefulsets, `ds` daemonsets, `rs` replicasets, `cm` configmaps, `ns` namespaces, `sa` serviceaccounts, `ing` ingresses, `pvc` persistentvolumeclaims, `pv` persistentvolumes, `no` nodes, `cj` cronjobs.

`describe` is the events and the state. `-o yaml` is the object. `-o wide` adds node and IP columns on pods.

```bash
$ kubectl get pods -l app=<name>
$ kubectl get pods --field-selector status.phase=Running
$ kubectl wait --for=condition=ready pod -l app=<name>
```

## Apply and delete

```bash
$ kubectl apply -f <file.yaml>
$ kubectl apply -f <directory>/
$ kubectl diff -f <file.yaml>
$ kubectl delete -f <file.yaml>
$ kubectl delete -f <file.yaml> --wait=false
$ kubectl kustomize <directory>/
$ kubectl apply -k <directory>/
```

`diff` prints what `apply` would change and changes nothing. `-k` applies a directory that contains `kustomization.yaml`.

A Deployment file `kubectl apply` will create:

```yaml
apiVersion: apps/v1
kind: Deployment
metadata:
  name: web
spec:
  replicas: 2
  selector:
    matchLabels:
      app: web
  template:
    metadata:
      labels:
        app: web
    spec:
      containers:
      - name: web
        image: nginx
        ports:
        - containerPort: 80
```

## Run, scale, roll

```bash
$ kubectl create deployment <name> --image=<image>
$ kubectl expose deployment <name> --port=80 --target-port=80
$ kubectl scale deployment <name> --replicas=3
$ kubectl autoscale deployment <name> --min=2 --max=5 --cpu-percent=80
$ kubectl set image deployment/<name> <container>=<image>:<tag>
$ kubectl rollout status deployment/<name>
$ kubectl rollout history deployment/<name>
$ kubectl rollout undo deployment/<name>
$ kubectl rollout undo deployment/<name> --to-revision=<n>
$ kubectl rollout restart deployment/<name>
$ kubectl rollout pause deployment/<name>
$ kubectl rollout resume deployment/<name>
```

`expose` creates a Service. `set image` changes the image and starts a rollout. `undo` returns to the previous revision, or to `--to-revision`. `restart` recreates the pods even when the spec did not change. `autoscale` creates a HorizontalPodAutoscaler. It has nothing to act on until metrics-server is installed.

```bash
$ kubectl create job <name> --image=<image> -- <command>
$ kubectl create cronjob <name> --image=<image> --schedule="*/5 * * * *" -- <command>
$ kubectl create job --from=cronjob/<name> <job-name>
$ kubectl get jobs,cronjobs
$ kubectl delete job <name>
$ kubectl delete cronjob <name>
```

The words after `--` are the container command.

## Logs, shell, files, forward

```bash
$ kubectl logs <pod>
$ kubectl logs -f --tail=100 <pod>
$ kubectl logs <pod> -c <container>
$ kubectl logs deploy/<name>
$ kubectl logs -l app=<name> --prefix
$ kubectl exec -it <pod> -- sh
$ kubectl exec -it <pod> -c <container> -- sh
$ kubectl exec <pod> -- <command>
$ kubectl port-forward pod/<pod> 8080:80
$ kubectl port-forward svc/<service> 8080:80
$ kubectl cp <pod>:/path ./local
$ kubectl cp ./local <pod>:/path
```

`-c` picks one container in a pod that has several. `port-forward` listens on your machine and sends that port to the pod. Ctrl-c stops it. `cp` copies a file in or out. The pod path comes first when copying out.

## Edit, label, annotate

```bash
$ kubectl edit deployment <name>
$ kubectl label pod <name> env=dev
$ kubectl label pod <name> env-
$ kubectl annotate pod <name> note=hello
$ kubectl annotate pod <name> note-
```

`edit` opens the object in `$EDITOR` and applies it on save. A trailing `-` on a label or annotation removes that key.

## Services, ingress, storage

```bash
$ kubectl get svc
$ kubectl describe svc <name>
$ kubectl get endpoints <name>
$ kubectl get ingress
$ kubectl describe ingress <name>
$ kubectl get pvc,pv,sc
$ kubectl describe pvc <name>
```

`endpoints` is the pod addresses a Service is sending traffic to. An empty list means the selector matched no ready pods.

## Config and secrets

```bash
$ kubectl create configmap <name> --from-literal=KEY=value
$ kubectl create configmap <name> --from-file=<path>
$ kubectl get configmap <name> -o yaml
$ kubectl delete configmap <name>
$ kubectl create secret generic <name> --from-literal=PASSWORD=<value>
$ kubectl create secret generic <name> --from-file=<path>
$ kubectl get secrets
$ kubectl get secret <name> -o yaml
$ kubectl delete secret <name>
```

A Secret's `data` values are base64, not hidden from anyone who can `get secrets` in that namespace. Decode one key you created:

```bash
$ kubectl get secret <name> -o jsonpath='{.data.PASSWORD}' | base64 -d
```

## Nodes

```bash
$ kubectl get nodes -o wide
$ kubectl describe node <name>
$ kubectl cordon <node>
$ kubectl uncordon <node>
$ kubectl drain <node> --ignore-daemonsets --delete-emptydir-data
```

`cordon` stops new pods from landing on the node. Pods already there keep running. `drain` cordons the node and evicts those pods. `uncordon` allows scheduling again.

## Who you are

```bash
$ kubectl auth whoami
$ kubectl auth can-i get pods
$ kubectl auth can-i create deployments -n <namespace>
$ kubectl get roles,rolebindings -n <namespace>
$ kubectl get clusterroles,clusterrolebindings
$ kubectl describe rolebinding <name> -n <namespace>
```

`can-i` answers whether the current credentials may do that. It does not grant anything.

## Resource use

```bash
$ kubectl top nodes
$ kubectl top pods
$ kubectl top pods -A --sort-by=cpu
```

`top` fails until a metrics server is installed. On minikube that is `minikube addons enable metrics-server`.

## Delete

```bash
$ kubectl delete pod <name>
$ kubectl delete deployment <name>
$ kubectl delete svc <name>
$ kubectl delete all -l app=<name>
```

Deleting a pod that a Deployment owns only recreates it. Delete the Deployment to remove those pods.

## Helm

Helm installs a chart as a named release.

```bash
$ helm repo add <name> <url>
$ helm repo update
$ helm repo list
$ helm repo remove <name>
$ helm search repo <chart>
$ helm show chart <name>/<chart>
$ helm show values <name>/<chart>
$ helm show all <name>/<chart>
$ helm template <release> <name>/<chart>
$ helm pull <name>/<chart>
```

`repo update` refreshes the chart index. `show values` prints the keys you can override. `template` renders the YAML and does not install it. `pull` downloads the chart archive.

```bash
$ helm install <release> <name>/<chart>
$ helm install <release> <name>/<chart> -n <namespace> --create-namespace
$ helm install <release> <name>/<chart> -f values.yaml
$ helm install <release> <name>/<chart> --set key=value
$ helm upgrade <release> <name>/<chart>
$ helm upgrade --install <release> <name>/<chart> -f values.yaml
$ helm list
$ helm list -A
$ helm status <release>
$ helm history <release>
$ helm get values <release>
$ helm get manifest <release>
$ helm rollback <release> <revision>
$ helm uninstall <release>
```

`upgrade --install` upgrades the release, or installs it if the name is new. `history` numbers the revisions. `rollback` returns to one of those numbers. `uninstall` removes the release. It does not remove PersistentVolumeClaims the chart created unless the chart says to.

## k9s

```bash
$ k9s
$ k9s -n <namespace>
$ k9s --context <context>
```

| Key | Effect |
| --- | ------ |
| `?` | Help |
| `:pods` | Pod view. Same pattern for `:deploy`, `:svc`, `:ns` |
| `/` | Filter the current view |
| `d` | Describe |
| `l` | Logs |
| `s` | Shell in the selected pod |
| Ctrl-d | Delete the selected object |
| `:q` | Quit |
