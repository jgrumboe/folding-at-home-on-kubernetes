# Folding at Home on Kubernetes

Fork of https://github.com/wind0r/k8s-supporting-folding-at-home to run in unprivileged contexts.

## Usage

To run the Folding@home client as a deployment with a single replica (one pod):

```
kubectl apply -f https://codeberg.org/hjacobs/folding-at-home-on-kubernetes/raw/branch/master/deploy/apply/deployment.yaml
```

You can edit the deployment afterwards to change the configuration (see below) and increase the number of replicas:

```
kubectl edit deploy folding-at-home
```

You can open the Folding@home web interface by forwarding port 7396 on your local machine:

```
kubectl port-forward $(kubectl get pod -l application=folding-at-home -o jsonpath="{.items[0].metadata.name}") 7396:7396
```

Now open http://localhost:7396/ in your browser.

## Configuration

Change the Folding@Home user and team ID via environment variables.
All settings are optional:

* `USER`: user name, defaults to "Anonymous"
* `TEAM`: team ID, defaults to "0"
* `PASSKEY`: optional, get one here: https://apps.foldingathome.org/getpasskey
* `POWER`: "light", "medium", or "full"



