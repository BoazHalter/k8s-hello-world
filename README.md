# K8S Hello-world 

## Overview
K8S Hello-world Is a GitHub repo that demonstrate a simple hello world application deployed on top of k8s using helm chart.

## Prerequisites
- kubernetes cluster
- helm 
- `kubectl create ns sample1`

## Into the chart

The application chart values.yaml contains more values the following are just sample.


|  Chart key         |             Chart value                   |    Description                                          |
|--------------------|-------------------------------------------|---------------------------------------------------------|
|  `replicaCount`    |                 `1`                       | the number of pods to run                               |
|  `app.link`        | `github.com/BoazHalter/k8s-hello-world`   | the redirect link                                       |
|  `app.route`       | `"/sample/"`                              | the app endpoint                                        |
|  `image.repository`| `digitalocean/flask-helloworld`           | the container image repo                                |
|  `image.tag`       | `"latest"`                                | the container image version                             |
|  `service.type`    | `LoadBalancer`                            | k8s service type Loadbalancer enable www inbound traffic|
|  `service.port`    | `80`                                      | k8s service type Loadbalancer port to listen            |


## Using ConfigMap

ConfigMap is mounted as file app.py that enable configuration of:
  - app.link 
  - app.route

Installing the chart <br />
`helm install khw -n sample1 k8s-hello-world-chart/ --set replicaCount=2`

Deleting the chart <br />
`helm del -n sample1 khw`
