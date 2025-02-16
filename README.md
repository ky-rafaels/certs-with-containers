# Examples on providing certificates in containers

## Purpose
Providing trusted CA bundles and certificates when working with microservices can be frustrating. The approach here I'd like to propose is to have only the certificates necessary for providing trust to repositories for installation artifacts when a container is built should be provided at time of container build in say a Dockerfile. All other certificates necessary for trust between services that are environment specific, should be provided via kubernetes CRDs. This provides flexibility for containers to be deployable across environments, easing the promotion between environments, removing redundant build tasks from images, and keeping build repos cleaner.

## Test Evironment Setup

Provision a kind cluster using the script [here](https://github.com/ky-rafaels/kind-cluster)

```bash
git clone https://github.com/ky-rafaels/kind-cluster
cd kind-cluster
./cilium-kind-deploy.sh 1 cluster1 us-east-1 us-east-1a
```

Clone this repo 

```bash
git clone git@github.com:ky-rafaels/certs-with-containers.git
cd certs-with-containers
```


## Examples

### Trust bundles

### JKS Certificates