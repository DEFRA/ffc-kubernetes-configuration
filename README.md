# FFC Kubernetes Configuration

Kubernetes configuration yaml files used in FFC clusters.

## Helm Charts

### ffc-workstream
Helm chart for configuring a new workstream namespace

`./helm/ffc-workstream`

Includes:
- Resource Quota
- Role Binding

#### Usage
This Helm chart uses the [FFC Helm Library](https://github.com/DEFRA/ffc-helm-library).

The chart's `values.yaml` contains example values that must be overriden with during helm install/upgrade commands to successfully create namespace resources.

Example values are provided below using the ffc-demo namespace.
```
name: ffc-demo
namespace: ffc-demo
workstream: ffc-demo
environment: production

labels:
  instance:
  version: 1.0.0
  component: ffc-demo

resourceQuota:
  requestCpu: "1"
  requestMemory: 1Gi
  limitCpu: "2"
  limitMemory: 2Gi
```

The chart can be applied to a cluster with the following commands, replacing `ffc-demo` with the name of the workstream:

```
kubectl create namespace ffc-demo
helm upgrade --install --atomic --namespace ffc-demo ffc-demo ./helm/ffc-workstream
```

The namespace can be removed with the following commands:

```
kubectl uninstall ffc-demo --namespace ffc-demo
kubectl delete namespace ffc-demo
```

## General Configuration

### Priority Classes

Priority classes help kubernetes understand which resources it would shut down in the event that it's over utilised.

Without Priority classes a default value of 0 is given and they would be the first closed during preemption.

There are 3 Priority levels:
High (with a value of 1000)
Default (with a value of 600)
Low (with a value of 200)

## Licence

THIS INFORMATION IS LICENSED UNDER THE CONDITIONS OF THE OPEN GOVERNMENT LICENCE found at:

http://www.nationalarchives.gov.uk/doc/open-government-licence/version/3

The following attribution statement MUST be cited in your products and applications when using this information.

>Contains public sector information licensed under the Open Government license v3

### About the licence
The Open Government Licence (OGL) was developed by the Controller of Her Majesty's Stationery Office (HMSO) to enable information providers in the public sector to license the use and re-use of their information under a common open licence.

It is designed to encourage use and re-use of information freely and flexibly, with only a few conditions.
