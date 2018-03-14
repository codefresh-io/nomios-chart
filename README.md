# Nomios

Nomios is a Codefresh DockerHub **trigger event provider** service.

## TL;DR

```sh
helm install codefresh/nomios
```

## Introduction

This chart bootstraps a [Hermes](https://github.com/codefresh-io/nomios) deployment on a [Kubernetes](http://kubernetes.io) cluster using the [Helm](https://helm.sh) package manager.

## Prerequisites

- Kubernetes 1.8+ with Beta APIs enabled
- Codefresh Helm Release
- Codefresh Hermes Service

## Installing the Chart

To install the chart with the release name `my-release`:

```sh
helm install --name my-release --namespace codefresh codefresh/nomios
```

The command deploys Nomios on the Kubernetes cluster in the `codefresh` namespace with default configuration. The [configuration](#configuration) section lists the parameters that can be configured during installation.

> **Tip**: List all releases using `helm list`

## Uninstalling the Chart

To uninstall/delete the `my-release` deployment:

```sh
helm delete my-release
```

The command removes all the Kubernetes components associated with the chart and deletes the release.

## Configuration

The following tables lists the configurable parameters of the Hermes chart and their default values.

| Parameter              | Description                                                      | Default                                                |
| ---------------------- | ---------------------------------------------------------------- | ------------------------------------------------------ |
| `image.repository`     | Hermes image                                                     | `codefresh/nomios`                                     |
| `image.tag`            | Hermes image tag                                                 | `0.4`                                                  |
| `image.PullPolicy`     | Image pull policy                                                | `IfNotPresent`                                         |
| `service.name`         | Kubernetes Service name                                          | `nomios`                                               |
| `service.type`         | Kubernetes Service type                                          | `NodePort`                                             |
| `service.externalPort` | Service external port                                            | `80`                                                   |
| `service.externalPort` | Service internal port                                            | `8080`                                                 |
| `logLevel`             | Log level: `debug`, `info`, `warning`, `error`, `fatal`, `panic` | `info`                                                 |
| `event.type`           | Trigger Event type (do not change)                               | `registry`                                             |
| `event.kind`           | Trigger Event kind (do not change)                               | `dockerhub`                                            |
| `event.action`         | Trigger Event event action name (do not change)                  | `push`                                                 |
| `hermesService`        | Hermes Service name                                              | `{{ .Release.Name }}-hermes`                           |
| `publicDnsName`        | Public DNS name used as root for external webhook URL            | `{{ .Values.global.appUrl}} or https://g.codefresh.io` |
| `ingress.enabled`      | Use Ingress Controller to expose webhook URL                     | `true`                                                 |
| `ingres.path`          | Ingress routing path                                             | `/nomios/*`                                            |