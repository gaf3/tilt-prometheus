# tilt-prometheus

A general Prometheus operator and instance to use locally with Kubernetes services

# Requirements

- A Mac (Linux might work, not sure)
- make (I think comes with xcode, git, etc)
- docker-desktop - Enabled Kubernetes (and disable Fuse)
- kubectl - https://kubernetes.io/docs/tasks/tools/install-kubectl/
- kustomize - https://kubectl.docs.kubernetes.io/installation/kustomize/
- tilt - https://docs.tilt.dev/install.html

# Configure

Services could require the Custom Resource Definitions (CRD) of Prometheus, if not Prometheus itself, to start properly. To install them:
- `make crd`

# Run

- `make up` - Starts Prometheus by firing up tilt, hit space to see the GUI, ctrl-c to exit
- `make down` - Cleans everything up

# Access

Make sure you `make up` before trying to access Prometheus or starting any k8s service needs it.

Hit space to bring up the web UI. You might see the 'prometheus' serive as red. Hit the refresh link next to it to turn it green. Click the `http://localhost:9090` link there to access prometheus.

From within kubernetes, host (DNS) is `db.prometheus` at port `9090`.
