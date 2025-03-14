<!--- app-name: Milvus -->

# Milvus packaged by Bitnami

Milvus is a cloud-native, open-source vector database solution for AI applications and similarity search. Features high scalability, hibrid search and unified lambda structure.

[Overview of Milvus](https://milvus.io/)

Trademarks: This software listing is packaged by Bitnami. The respective trademarks mentioned in the offering are owned by the respective companies, and use of them does not imply any affiliation or endorsement.

## TL;DR

```console
helm install my-release oci://REGISTRY_NAME/REPOSITORY_NAME/milvus
```

> Note: You need to substitute the placeholders `REGISTRY_NAME` and `REPOSITORY_NAME` with a reference to your Helm chart registry and repository. For example, in the case of Bitnami, you need to use `REGISTRY_NAME=registry-1.docker.io` and `REPOSITORY_NAME=bitnamicharts`.

## Introduction

Bitnami charts for Helm are carefully engineered, actively maintained and are the quickest and easiest way to deploy containers on a Kubernetes cluster that are ready to handle production workloads.

This chart bootstraps a [Milvus](https://github.com/grafana/loki) Deployment in a [Kubernetes](https://kubernetes.io) cluster using the [Helm](https://helm.sh) package manager.

Bitnami charts can be used with [Kubeapps](https://kubeapps.dev/) for deployment and management of Helm Charts in clusters.

[Learn more about the default configuration of the chart](https://docs.bitnami.com/kubernetes/infrastructure/milvus/get-started/).

Looking to use Milvus in production? Try [VMware Tanzu Application Catalog](https://bitnami.com/enterprise), the enterprise edition of Bitnami Application Catalog.

## Prerequisites

- Kubernetes 1.23+
- Helm 3.8.0+
- PV provisioner support in the underlying infrastructure

## Installing the Chart

To install the chart with the release name `my-release`:

```console
helm install my-release oci://REGISTRY_NAME/REPOSITORY_NAME/milvus
```

> Note: You need to substitute the placeholders `REGISTRY_NAME` and `REPOSITORY_NAME` with a reference to your Helm chart registry and repository. For example, in the case of Bitnami, you need to use `REGISTRY_NAME=registry-1.docker.io` and `REPOSITORY_NAME=bitnamicharts`.

The command deploys milvus on the Kubernetes cluster in the default configuration. The [Parameters](#parameters) section lists the parameters that can be configured during installation.

> **Tip**: List all releases using `helm list`

## Uninstalling the Chart

To uninstall/delete the `my-release` deployment:

```console
helm delete my-release
```

The command removes all the Kubernetes components associated with the chart and deletes the release.

## Parameters

### Global parameters

| Name                      | Description                                     | Value |
| ------------------------- | ----------------------------------------------- | ----- |
| `global.imageRegistry`    | Global Docker image registry                    | `""`  |
| `global.imagePullSecrets` | Global Docker registry secret names as an array | `[]`  |
| `global.storageClass`     | Global StorageClass for Persistent Volume(s)    | `""`  |

### Common parameters

| Name                     | Description                                                                             | Value           |
| ------------------------ | --------------------------------------------------------------------------------------- | --------------- |
| `kubeVersion`            | Override Kubernetes version                                                             | `""`            |
| `nameOverride`           | String to partially override common.names.fullname                                      | `""`            |
| `fullnameOverride`       | String to fully override common.names.fullname                                          | `""`            |
| `commonLabels`           | Labels to add to all deployed objects                                                   | `{}`            |
| `commonAnnotations`      | Annotations to add to all deployed objects                                              | `{}`            |
| `clusterDomain`          | Kubernetes cluster domain name                                                          | `cluster.local` |
| `extraDeploy`            | Array of extra objects to deploy with the release                                       | `[]`            |
| `diagnosticMode.enabled` | Enable diagnostic mode (all probes will be disabled and the command will be overridden) | `false`         |
| `diagnosticMode.command` | Command to override all containers in the deployments/statefulsets                      | `["sleep"]`     |
| `diagnosticMode.args`    | Args to override all containers in the deployments/statefulsets                         | `["infinity"]`  |

### Common Milvus Parameters

| Name                                                        | Description                                                                                                                                         | Value                      |
| ----------------------------------------------------------- | --------------------------------------------------------------------------------------------------------------------------------------------------- | -------------------------- |
| `milvus.image.registry`                                     | Milvus image registry                                                                                                                               | `REGISTRY_NAME`            |
| `milvus.image.repository`                                   | Milvus image repository                                                                                                                             | `REPOSITORY_NAME/milvus`   |
| `milvus.image.digest`                                       | Milvus image digest in the way sha256:aa.... Please note this parameter, if set, will override the tag                                              | `""`                       |
| `milvus.image.pullPolicy`                                   | Milvus image pull policy                                                                                                                            | `IfNotPresent`             |
| `milvus.image.pullSecrets`                                  | Milvus image pull secrets                                                                                                                           | `[]`                       |
| `milvus.image.debug`                                        | Enable debug mode                                                                                                                                   | `false`                    |
| `milvus.auth.enabled`                                       | enable Milvus authentication                                                                                                                        | `false`                    |
| `milvus.auth.username`                                      | Milvus username                                                                                                                                     | `user`                     |
| `milvus.auth.password`                                      | Milvus username password                                                                                                                            | `""`                       |
| `milvus.auth.rootPassword`                                  | Milvus root password                                                                                                                                | `""`                       |
| `milvus.auth.existingSecret`                                | Name of a secret containing the Milvus password                                                                                                     | `""`                       |
| `milvus.auth.existingSecretPasswordKey`                     | Name of the secret key containing the Milvus password                                                                                               | `""`                       |
| `milvus.defaultConfig`                                      | Milvus components default configuration                                                                                                             | `""`                       |
| `milvus.extraConfig`                                        | Extra configuration parameters                                                                                                                      | `{}`                       |
| `milvus.existingConfigMap`                                  | name of a ConfigMap with existing configuration for the default configuration                                                                       | `""`                       |
| `milvus.extraConfigExistingConfigMap`                       | name of a ConfigMap with existing configuration for the Dashboard                                                                                   | `""`                       |
| `initJob.forceRun`                                          | Force the run of the credential job                                                                                                                 | `false`                    |
| `initJob.image.registry`                                    | PyMilvus image registry                                                                                                                             | `REGISTRY_NAME`            |
| `initJob.image.repository`                                  | PyMilvus image repository                                                                                                                           | `REPOSITORY_NAME/pymilvus` |
| `initJob.image.digest`                                      | PyMilvus image digest in the way sha256:aa.... Please note this parameter, if set, will override the tag image tag (immutable tags are recommended) | `""`                       |
| `initJob.image.pullPolicy`                                  | PyMilvus image pull policy                                                                                                                          | `IfNotPresent`             |
| `initJob.image.pullSecrets`                                 | PyMilvus image pull secrets                                                                                                                         | `[]`                       |
| `initJob.enableDefaultInitContainers`                       | Deploy default init containers                                                                                                                      | `true`                     |
| `initJob.backoffLimit`                                      | set backoff limit of the job                                                                                                                        | `10`                       |
| `initJob.extraVolumes`                                      | Optionally specify extra list of additional volumes for the credential init job                                                                     | `[]`                       |
| `initJob.extraCommands`                                     | Extra commands to pass to the generation job                                                                                                        | `""`                       |
| `initJob.containerSecurityContext.enabled`                  | Enabled containers' Security Context                                                                                                                | `true`                     |
| `initJob.containerSecurityContext.runAsUser`                | Set containers' Security Context runAsUser                                                                                                          | `1001`                     |
| `initJob.containerSecurityContext.runAsNonRoot`             | Set container's Security Context runAsNonRoot                                                                                                       | `true`                     |
| `initJob.containerSecurityContext.privileged`               | Set container's Security Context privileged                                                                                                         | `false`                    |
| `initJob.containerSecurityContext.readOnlyRootFilesystem`   | Set container's Security Context readOnlyRootFilesystem                                                                                             | `true`                     |
| `initJob.containerSecurityContext.allowPrivilegeEscalation` | Set container's Security Context allowPrivilegeEscalation                                                                                           | `false`                    |
| `initJob.containerSecurityContext.capabilities.drop`        | List of capabilities to be dropped                                                                                                                  | `["ALL"]`                  |
| `initJob.containerSecurityContext.seccompProfile.type`      | Set container's Security Context seccomp profile                                                                                                    | `RuntimeDefault`           |
| `initJob.podSecurityContext.enabled`                        | Enabled credential init job pods' Security Context                                                                                                  | `true`                     |
| `initJob.podSecurityContext.fsGroup`                        | Set credential init job pod's Security Context fsGroup                                                                                              | `1001`                     |
| `initJob.extraEnvVars`                                      | Array containing extra env vars to configure the credential init job                                                                                | `[]`                       |
| `initJob.extraEnvVarsCM`                                    | ConfigMap containing extra env vars to configure the credential init job                                                                            | `""`                       |
| `initJob.extraEnvVarsSecret`                                | Secret containing extra env vars to configure the credential init job (in case of sensitive data)                                                   | `""`                       |
| `initJob.extraVolumeMounts`                                 | Array of extra volume mounts to be added to the jwt Container (evaluated as template). Normally used with `extraVolumes`.                           | `[]`                       |
| `initJob.resources.limits`                                  | The resources limits for the container                                                                                                              | `{}`                       |
| `initJob.resources.requests`                                | The requested resources for the container                                                                                                           | `{}`                       |
| `initJob.hostAliases`                                       | Add deployment host aliases                                                                                                                         | `[]`                       |
| `initJob.annotations`                                       | Add annotations to the job                                                                                                                          | `{}`                       |
| `initJob.podLabels`                                         | Additional pod labels                                                                                                                               | `{}`                       |
| `initJob.podAnnotations`                                    | Additional pod annotations                                                                                                                          | `{}`                       |

### Data Coordinator Deployment Parameters

| Name                                                          | Description                                                                                                | Value            |
| ------------------------------------------------------------- | ---------------------------------------------------------------------------------------------------------- | ---------------- |
| `dataCoord.enabled`                                           | Enable Data Coordinator deployment                                                                         | `true`           |
| `dataCoord.extraEnvVars`                                      | Array with extra environment variables to add to data coordinator nodes                                    | `[]`             |
| `dataCoord.extraEnvVarsCM`                                    | Name of existing ConfigMap containing extra env vars for data coordinator nodes                            | `""`             |
| `dataCoord.extraEnvVarsSecret`                                | Name of existing Secret containing extra env vars for data coordinator nodes                               | `""`             |
| `dataCoord.defaultConfig`                                     | Default override configuration from the common set in milvus.defaultConfig                                 | `""`             |
| `dataCoord.existingConfigMap`                                 | name of a ConfigMap with existing configuration for the default configuration                              | `""`             |
| `dataCoord.extraConfig`                                       | Override configuration                                                                                     | `{}`             |
| `dataCoord.extraConfigExistingConfigMap`                      | name of a ConfigMap with existing configuration for the Dashboard                                          | `""`             |
| `dataCoord.command`                                           | Override default container command (useful when using custom images)                                       | `[]`             |
| `dataCoord.args`                                              | Override default container args (useful when using custom images)                                          | `[]`             |
| `dataCoord.replicaCount`                                      | Number of Data Coordinator replicas to deploy                                                              | `1`              |
| `dataCoord.containerPorts.grpc`                               | GRPC port for Data Coordinator                                                                             | `19530`          |
| `dataCoord.containerPorts.metrics`                            | Metrics port for Data Coordinator                                                                          | `9091`           |
| `dataCoord.livenessProbe.enabled`                             | Enable livenessProbe on Data Coordinator nodes                                                             | `true`           |
| `dataCoord.livenessProbe.initialDelaySeconds`                 | Initial delay seconds for livenessProbe                                                                    | `5`              |
| `dataCoord.livenessProbe.periodSeconds`                       | Period seconds for livenessProbe                                                                           | `10`             |
| `dataCoord.livenessProbe.timeoutSeconds`                      | Timeout seconds for livenessProbe                                                                          | `5`              |
| `dataCoord.livenessProbe.failureThreshold`                    | Failure threshold for livenessProbe                                                                        | `5`              |
| `dataCoord.livenessProbe.successThreshold`                    | Success threshold for livenessProbe                                                                        | `1`              |
| `dataCoord.readinessProbe.enabled`                            | Enable readinessProbe on Data Coordinator nodes                                                            | `true`           |
| `dataCoord.readinessProbe.initialDelaySeconds`                | Initial delay seconds for readinessProbe                                                                   | `5`              |
| `dataCoord.readinessProbe.periodSeconds`                      | Period seconds for readinessProbe                                                                          | `10`             |
| `dataCoord.readinessProbe.timeoutSeconds`                     | Timeout seconds for readinessProbe                                                                         | `5`              |
| `dataCoord.readinessProbe.failureThreshold`                   | Failure threshold for readinessProbe                                                                       | `5`              |
| `dataCoord.readinessProbe.successThreshold`                   | Success threshold for readinessProbe                                                                       | `1`              |
| `dataCoord.startupProbe.enabled`                              | Enable startupProbe on Data Coordinator containers                                                         | `false`          |
| `dataCoord.startupProbe.initialDelaySeconds`                  | Initial delay seconds for startupProbe                                                                     | `5`              |
| `dataCoord.startupProbe.periodSeconds`                        | Period seconds for startupProbe                                                                            | `10`             |
| `dataCoord.startupProbe.timeoutSeconds`                       | Timeout seconds for startupProbe                                                                           | `5`              |
| `dataCoord.startupProbe.failureThreshold`                     | Failure threshold for startupProbe                                                                         | `5`              |
| `dataCoord.startupProbe.successThreshold`                     | Success threshold for startupProbe                                                                         | `1`              |
| `dataCoord.customLivenessProbe`                               | Custom livenessProbe that overrides the default one                                                        | `{}`             |
| `dataCoord.customReadinessProbe`                              | Custom readinessProbe that overrides the default one                                                       | `{}`             |
| `dataCoord.customStartupProbe`                                | Custom startupProbe that overrides the default one                                                         | `{}`             |
| `dataCoord.resources.limits`                                  | The resources limits for the data coordinator containers                                                   | `{}`             |
| `dataCoord.resources.requests`                                | The requested resources for the data coordinator containers                                                | `{}`             |
| `dataCoord.podSecurityContext.enabled`                        | Enabled Data Coordinator pods' Security Context                                                            | `true`           |
| `dataCoord.podSecurityContext.fsGroup`                        | Set Data Coordinator pod's Security Context fsGroup                                                        | `1001`           |
| `dataCoord.containerSecurityContext.enabled`                  | Enabled containers' Security Context                                                                       | `true`           |
| `dataCoord.containerSecurityContext.runAsUser`                | Set containers' Security Context runAsUser                                                                 | `1001`           |
| `dataCoord.containerSecurityContext.runAsNonRoot`             | Set container's Security Context runAsNonRoot                                                              | `true`           |
| `dataCoord.containerSecurityContext.privileged`               | Set container's Security Context privileged                                                                | `false`          |
| `dataCoord.containerSecurityContext.readOnlyRootFilesystem`   | Set container's Security Context readOnlyRootFilesystem                                                    | `true`           |
| `dataCoord.containerSecurityContext.allowPrivilegeEscalation` | Set container's Security Context allowPrivilegeEscalation                                                  | `false`          |
| `dataCoord.containerSecurityContext.capabilities.drop`        | List of capabilities to be dropped                                                                         | `["ALL"]`        |
| `dataCoord.containerSecurityContext.seccompProfile.type`      | Set container's Security Context seccomp profile                                                           | `RuntimeDefault` |
| `dataCoord.lifecycleHooks`                                    | for the data coordinator container(s) to automate configuration before or after startup                    | `{}`             |
| `dataCoord.runtimeClassName`                                  | Name of the runtime class to be used by pod(s)                                                             | `""`             |
| `dataCoord.hostAliases`                                       | data coordinator pods host aliases                                                                         | `[]`             |
| `dataCoord.podLabels`                                         | Extra labels for data coordinator pods                                                                     | `{}`             |
| `dataCoord.podAnnotations`                                    | Annotations for data coordinator pods                                                                      | `{}`             |
| `dataCoord.podAffinityPreset`                                 | Pod affinity preset. Ignored if `data coordinator.affinity` is set. Allowed values: `soft` or `hard`       | `""`             |
| `dataCoord.podAntiAffinityPreset`                             | Pod anti-affinity preset. Ignored if `data coordinator.affinity` is set. Allowed values: `soft` or `hard`  | `soft`           |
| `dataCoord.nodeAffinityPreset.type`                           | Node affinity preset type. Ignored if `data coordinator.affinity` is set. Allowed values: `soft` or `hard` | `""`             |
| `dataCoord.nodeAffinityPreset.key`                            | Node label key to match. Ignored if `data coordinator.affinity` is set                                     | `""`             |
| `dataCoord.nodeAffinityPreset.values`                         | Node label values to match. Ignored if `data coordinator.affinity` is set                                  | `[]`             |
| `dataCoord.affinity`                                          | Affinity for Data Coordinator pods assignment                                                              | `{}`             |
| `dataCoord.nodeSelector`                                      | Node labels for Data Coordinator pods assignment                                                           | `{}`             |
| `dataCoord.tolerations`                                       | Tolerations for Data Coordinator pods assignment                                                           | `[]`             |
| `dataCoord.topologySpreadConstraints`                         | Topology Spread Constraints for pod assignment spread across your cluster among failure-domains            | `[]`             |
| `dataCoord.priorityClassName`                                 | Data Coordinator pods' priorityClassName                                                                   | `""`             |
| `dataCoord.schedulerName`                                     | Kubernetes pod scheduler registry                                                                          | `""`             |
| `dataCoord.updateStrategy.type`                               | Data Coordinator statefulset strategy type                                                                 | `RollingUpdate`  |
| `dataCoord.updateStrategy.rollingUpdate`                      | Data Coordinator statefulset rolling update configuration parameters                                       | `{}`             |
| `dataCoord.extraVolumes`                                      | Optionally specify extra list of additional volumes for the Data Coordinator pod(s)                        | `[]`             |
| `dataCoord.extraVolumeMounts`                                 | Optionally specify extra list of additional volumeMounts for the Data Coordinator container(s)             | `[]`             |
| `dataCoord.sidecars`                                          | Add additional sidecar containers to the Data Coordinator pod(s)                                           | `[]`             |
| `dataCoord.enableDefaultInitContainers`                       | Deploy default init containers                                                                             | `true`           |
| `dataCoord.initContainers`                                    | Add additional init containers to the Data Coordinator pod(s)                                              | `[]`             |
| `dataCoord.serviceAccount.create`                             | Enable creation of ServiceAccount for Data Coordinator pods                                                | `false`          |
| `dataCoord.serviceAccount.name`                               | The name of the ServiceAccount to use                                                                      | `""`             |
| `dataCoord.serviceAccount.automountServiceAccountToken`       | Allows auto mount of ServiceAccountToken on the serviceAccount created                                     | `false`          |
| `dataCoord.serviceAccount.annotations`                        | Additional custom annotations for the ServiceAccount                                                       | `{}`             |
| `dataCoord.pdb.create`                                        | Enable/disable a Pod Disruption Budget creation                                                            | `false`          |
| `dataCoord.pdb.minAvailable`                                  | Minimum number/percentage of pods that should remain scheduled                                             | `1`              |
| `dataCoord.pdb.maxUnavailable`                                | Maximum number/percentage of pods that may be made unavailable                                             | `""`             |

### Data Coordinator Autoscaling configuration

| Name                                                | Description                                                                                                                                                            | Value   |
| --------------------------------------------------- | ---------------------------------------------------------------------------------------------------------------------------------------------------------------------- | ------- |
| `dataCoord.autoscaling.vpa.enabled`                 | Enable VPA                                                                                                                                                             | `false` |
| `dataCoord.autoscaling.vpa.annotations`             | Annotations for VPA resource                                                                                                                                           | `{}`    |
| `dataCoord.autoscaling.vpa.controlledResources`     | VPA List of resources that the vertical pod autoscaler can control. Defaults to cpu and memory                                                                         | `[]`    |
| `dataCoord.autoscaling.vpa.maxAllowed`              | VPA Max allowed resources for the pod                                                                                                                                  | `{}`    |
| `dataCoord.autoscaling.vpa.minAllowed`              | VPA Min allowed resources for the pod                                                                                                                                  | `{}`    |
| `dataCoord.autoscaling.vpa.updatePolicy.updateMode` | Autoscaling update policy Specifies whether recommended updates are applied when a Pod is started and whether recommended updates are applied during the life of a Pod | `Auto`  |
| `dataCoord.autoscaling.hpa.enabled`                 | Enable HPA for Milvus Data Plane                                                                                                                                       | `false` |
| `dataCoord.autoscaling.hpa.annotations`             | Annotations for HPA resource                                                                                                                                           | `{}`    |
| `dataCoord.autoscaling.hpa.minReplicas`             | Minimum number of Milvus Data Plane replicas                                                                                                                           | `""`    |
| `dataCoord.autoscaling.hpa.maxReplicas`             | Maximum number of Milvus Data Plane replicas                                                                                                                           | `""`    |
| `dataCoord.autoscaling.hpa.targetCPU`               | Target CPU utilization percentage                                                                                                                                      | `""`    |
| `dataCoord.autoscaling.hpa.targetMemory`            | Target Memory utilization percentage                                                                                                                                   | `""`    |

### Data Coordinator Traffic Exposure Parameters

| Name                                              | Description                                                      | Value       |
| ------------------------------------------------- | ---------------------------------------------------------------- | ----------- |
| `dataCoord.service.type`                          | Data Coordinator service type                                    | `ClusterIP` |
| `dataCoord.service.ports.grpc`                    | Data Coordinator GRPC service port                               | `19530`     |
| `dataCoord.service.ports.metrics`                 | Data Coordinator Metrics service port                            | `9091`      |
| `dataCoord.service.nodePorts.grpc`                | Node port for GRPC                                               | `""`        |
| `dataCoord.service.nodePorts.metrics`             | Node port for Metrics                                            | `""`        |
| `dataCoord.service.sessionAffinityConfig`         | Additional settings for the sessionAffinity                      | `{}`        |
| `dataCoord.service.sessionAffinity`               | Control where client requests go, to the same pod or round-robin | `None`      |
| `dataCoord.service.clusterIP`                     | Data Coordinator service Cluster IP                              | `""`        |
| `dataCoord.service.loadBalancerIP`                | Data Coordinator service Load Balancer IP                        | `""`        |
| `dataCoord.service.loadBalancerSourceRanges`      | Data Coordinator service Load Balancer sources                   | `[]`        |
| `dataCoord.service.externalTrafficPolicy`         | Data Coordinator service external traffic policy                 | `Cluster`   |
| `dataCoord.service.annotations`                   | Additional custom annotations for Data Coordinator service       | `{}`        |
| `dataCoord.service.extraPorts`                    | Extra ports to expose in the Data Coordinator service            | `[]`        |
| `dataCoord.networkPolicy.enabled`                 | Enable creation of NetworkPolicy resources                       | `false`     |
| `dataCoord.networkPolicy.allowExternal`           | The Policy model to apply                                        | `true`      |
| `dataCoord.networkPolicy.extraIngress`            | Add extra ingress rules to the NetworkPolicy                     | `[]`        |
| `dataCoord.networkPolicy.extraEgress`             | Add extra ingress rules to the NetworkPolicy                     | `[]`        |
| `dataCoord.networkPolicy.ingressNSMatchLabels`    | Labels to match to allow traffic from other namespaces           | `{}`        |
| `dataCoord.networkPolicy.ingressNSPodMatchLabels` | Pod labels to match to allow traffic from other namespaces       | `{}`        |

### Data Coordinator Metrics Parameters

| Name                                                 | Description                                                                           | Value   |
| ---------------------------------------------------- | ------------------------------------------------------------------------------------- | ------- |
| `dataCoord.metrics.enabled`                          | Enable metrics                                                                        | `false` |
| `dataCoord.metrics.annotations`                      | Annotations for the server service in order to scrape metrics                         | `{}`    |
| `dataCoord.metrics.serviceMonitor.enabled`           | Create ServiceMonitor Resource for scraping metrics using Prometheus Operator         | `false` |
| `dataCoord.metrics.serviceMonitor.annotations`       | Annotations for the ServiceMonitor Resource                                           | `""`    |
| `dataCoord.metrics.serviceMonitor.namespace`         | Namespace for the ServiceMonitor Resource (defaults to the Release Namespace)         | `""`    |
| `dataCoord.metrics.serviceMonitor.interval`          | Interval at which metrics should be scraped.                                          | `""`    |
| `dataCoord.metrics.serviceMonitor.scrapeTimeout`     | Timeout after which the scrape is ended                                               | `""`    |
| `dataCoord.metrics.serviceMonitor.labels`            | Additional labels that can be used so ServiceMonitor will be discovered by Prometheus | `{}`    |
| `dataCoord.metrics.serviceMonitor.selector`          | Prometheus instance selector labels                                                   | `{}`    |
| `dataCoord.metrics.serviceMonitor.relabelings`       | RelabelConfigs to apply to samples before scraping                                    | `[]`    |
| `dataCoord.metrics.serviceMonitor.metricRelabelings` | MetricRelabelConfigs to apply to samples before ingestion                             | `[]`    |
| `dataCoord.metrics.serviceMonitor.honorLabels`       | Specify honorLabels parameter to add the scrape endpoint                              | `false` |
| `dataCoord.metrics.serviceMonitor.jobLabel`          | The name of the label on the target service to use as the job name in prometheus.     | `""`    |

### Root Coordinator Deployment Parameters

| Name                                                          | Description                                                                                                | Value            |
| ------------------------------------------------------------- | ---------------------------------------------------------------------------------------------------------- | ---------------- |
| `rootCoord.enabled`                                           | Enable Root Coordinator deployment                                                                         | `true`           |
| `rootCoord.extraEnvVars`                                      | Array with extra environment variables to add to data coordinator nodes                                    | `[]`             |
| `rootCoord.extraEnvVarsCM`                                    | Name of existing ConfigMap containing extra env vars for data coordinator nodes                            | `""`             |
| `rootCoord.extraEnvVarsSecret`                                | Name of existing Secret containing extra env vars for data coordinator nodes                               | `""`             |
| `rootCoord.defaultConfig`                                     | Default override configuration from the common set in milvus.defaultConfig                                 | `""`             |
| `rootCoord.existingConfigMap`                                 | name of a ConfigMap with existing configuration for the default configuration                              | `""`             |
| `rootCoord.extraConfig`                                       | Override configuration                                                                                     | `{}`             |
| `rootCoord.extraConfigExistingConfigMap`                      | name of a ConfigMap with existing configuration for the Dashboard                                          | `""`             |
| `rootCoord.command`                                           | Override default container command (useful when using custom images)                                       | `[]`             |
| `rootCoord.args`                                              | Override default container args (useful when using custom images)                                          | `[]`             |
| `rootCoord.replicaCount`                                      | Number of Root Coordinator replicas to deploy                                                              | `1`              |
| `rootCoord.containerPorts.grpc`                               | GRPC port for Root Coordinator                                                                             | `19530`          |
| `rootCoord.containerPorts.metrics`                            | Metrics port for Root Coordinator                                                                          | `9091`           |
| `rootCoord.livenessProbe.enabled`                             | Enable livenessProbe on Root Coordinator nodes                                                             | `true`           |
| `rootCoord.livenessProbe.initialDelaySeconds`                 | Initial delay seconds for livenessProbe                                                                    | `5`              |
| `rootCoord.livenessProbe.periodSeconds`                       | Period seconds for livenessProbe                                                                           | `10`             |
| `rootCoord.livenessProbe.timeoutSeconds`                      | Timeout seconds for livenessProbe                                                                          | `5`              |
| `rootCoord.livenessProbe.failureThreshold`                    | Failure threshold for livenessProbe                                                                        | `5`              |
| `rootCoord.livenessProbe.successThreshold`                    | Success threshold for livenessProbe                                                                        | `1`              |
| `rootCoord.readinessProbe.enabled`                            | Enable readinessProbe on Root Coordinator nodes                                                            | `true`           |
| `rootCoord.readinessProbe.initialDelaySeconds`                | Initial delay seconds for readinessProbe                                                                   | `5`              |
| `rootCoord.readinessProbe.periodSeconds`                      | Period seconds for readinessProbe                                                                          | `10`             |
| `rootCoord.readinessProbe.timeoutSeconds`                     | Timeout seconds for readinessProbe                                                                         | `5`              |
| `rootCoord.readinessProbe.failureThreshold`                   | Failure threshold for readinessProbe                                                                       | `5`              |
| `rootCoord.readinessProbe.successThreshold`                   | Success threshold for readinessProbe                                                                       | `1`              |
| `rootCoord.startupProbe.enabled`                              | Enable startupProbe on Root Coordinator containers                                                         | `false`          |
| `rootCoord.startupProbe.initialDelaySeconds`                  | Initial delay seconds for startupProbe                                                                     | `5`              |
| `rootCoord.startupProbe.periodSeconds`                        | Period seconds for startupProbe                                                                            | `10`             |
| `rootCoord.startupProbe.timeoutSeconds`                       | Timeout seconds for startupProbe                                                                           | `5`              |
| `rootCoord.startupProbe.failureThreshold`                     | Failure threshold for startupProbe                                                                         | `5`              |
| `rootCoord.startupProbe.successThreshold`                     | Success threshold for startupProbe                                                                         | `1`              |
| `rootCoord.customLivenessProbe`                               | Custom livenessProbe that overrides the default one                                                        | `{}`             |
| `rootCoord.customReadinessProbe`                              | Custom readinessProbe that overrides the default one                                                       | `{}`             |
| `rootCoord.customStartupProbe`                                | Custom startupProbe that overrides the default one                                                         | `{}`             |
| `rootCoord.resources.limits`                                  | The resources limits for the data coordinator containers                                                   | `{}`             |
| `rootCoord.resources.requests`                                | The requested resources for the data coordinator containers                                                | `{}`             |
| `rootCoord.podSecurityContext.enabled`                        | Enabled Root Coordinator pods' Security Context                                                            | `true`           |
| `rootCoord.podSecurityContext.fsGroup`                        | Set Root Coordinator pod's Security Context fsGroup                                                        | `1001`           |
| `rootCoord.containerSecurityContext.enabled`                  | Enabled containers' Security Context                                                                       | `true`           |
| `rootCoord.containerSecurityContext.runAsUser`                | Set containers' Security Context runAsUser                                                                 | `1001`           |
| `rootCoord.containerSecurityContext.runAsNonRoot`             | Set container's Security Context runAsNonRoot                                                              | `true`           |
| `rootCoord.containerSecurityContext.privileged`               | Set container's Security Context privileged                                                                | `false`          |
| `rootCoord.containerSecurityContext.readOnlyRootFilesystem`   | Set container's Security Context readOnlyRootFilesystem                                                    | `true`           |
| `rootCoord.containerSecurityContext.allowPrivilegeEscalation` | Set container's Security Context allowPrivilegeEscalation                                                  | `false`          |
| `rootCoord.containerSecurityContext.capabilities.drop`        | List of capabilities to be dropped                                                                         | `["ALL"]`        |
| `rootCoord.containerSecurityContext.seccompProfile.type`      | Set container's Security Context seccomp profile                                                           | `RuntimeDefault` |
| `rootCoord.lifecycleHooks`                                    | for the data coordinator container(s) to automate configuration before or after startup                    | `{}`             |
| `rootCoord.runtimeClassName`                                  | Name of the runtime class to be used by pod(s)                                                             | `""`             |
| `rootCoord.hostAliases`                                       | data coordinator pods host aliases                                                                         | `[]`             |
| `rootCoord.podLabels`                                         | Extra labels for data coordinator pods                                                                     | `{}`             |
| `rootCoord.podAnnotations`                                    | Annotations for data coordinator pods                                                                      | `{}`             |
| `rootCoord.podAffinityPreset`                                 | Pod affinity preset. Ignored if `data coordinator.affinity` is set. Allowed values: `soft` or `hard`       | `""`             |
| `rootCoord.podAntiAffinityPreset`                             | Pod anti-affinity preset. Ignored if `data coordinator.affinity` is set. Allowed values: `soft` or `hard`  | `soft`           |
| `rootCoord.nodeAffinityPreset.type`                           | Node affinity preset type. Ignored if `data coordinator.affinity` is set. Allowed values: `soft` or `hard` | `""`             |
| `rootCoord.nodeAffinityPreset.key`                            | Node label key to match. Ignored if `data coordinator.affinity` is set                                     | `""`             |
| `rootCoord.nodeAffinityPreset.values`                         | Node label values to match. Ignored if `data coordinator.affinity` is set                                  | `[]`             |
| `rootCoord.affinity`                                          | Affinity for Root Coordinator pods assignment                                                              | `{}`             |
| `rootCoord.nodeSelector`                                      | Node labels for Root Coordinator pods assignment                                                           | `{}`             |
| `rootCoord.tolerations`                                       | Tolerations for Root Coordinator pods assignment                                                           | `[]`             |
| `rootCoord.topologySpreadConstraints`                         | Topology Spread Constraints for pod assignment spread across your cluster among failure-domains            | `[]`             |
| `rootCoord.priorityClassName`                                 | Root Coordinator pods' priorityClassName                                                                   | `""`             |
| `rootCoord.schedulerName`                                     | Kubernetes pod scheduler registry                                                                          | `""`             |
| `rootCoord.updateStrategy.type`                               | Root Coordinator statefulset strategy type                                                                 | `RollingUpdate`  |
| `rootCoord.updateStrategy.rollingUpdate`                      | Root Coordinator statefulset rolling update configuration parameters                                       | `{}`             |
| `rootCoord.extraVolumes`                                      | Optionally specify extra list of additional volumes for the Root Coordinator pod(s)                        | `[]`             |
| `rootCoord.extraVolumeMounts`                                 | Optionally specify extra list of additional volumeMounts for the Root Coordinator container(s)             | `[]`             |
| `rootCoord.sidecars`                                          | Add additional sidecar containers to the Root Coordinator pod(s)                                           | `[]`             |
| `rootCoord.enableDefaultInitContainers`                       | Deploy default init containers                                                                             | `true`           |
| `rootCoord.initContainers`                                    | Add additional init containers to the Root Coordinator pod(s)                                              | `[]`             |
| `rootCoord.serviceAccount.create`                             | Enable creation of ServiceAccount for Root Coordinator pods                                                | `false`          |
| `rootCoord.serviceAccount.name`                               | The name of the ServiceAccount to use                                                                      | `""`             |
| `rootCoord.serviceAccount.automountServiceAccountToken`       | Allows auto mount of ServiceAccountToken on the serviceAccount created                                     | `false`          |
| `rootCoord.serviceAccount.annotations`                        | Additional custom annotations for the ServiceAccount                                                       | `{}`             |
| `rootCoord.pdb.create`                                        | Enable/disable a Pod Disruption Budget creation                                                            | `false`          |
| `rootCoord.pdb.minAvailable`                                  | Minimum number/percentage of pods that should remain scheduled                                             | `1`              |
| `rootCoord.pdb.maxUnavailable`                                | Maximum number/percentage of pods that may be made unavailable                                             | `""`             |

### Root Coordinator Autoscaling configuration

| Name                                                | Description                                                                                                                                                            | Value   |
| --------------------------------------------------- | ---------------------------------------------------------------------------------------------------------------------------------------------------------------------- | ------- |
| `rootCoord.autoscaling.vpa.enabled`                 | Enable VPA                                                                                                                                                             | `false` |
| `rootCoord.autoscaling.vpa.annotations`             | Annotations for VPA resource                                                                                                                                           | `{}`    |
| `rootCoord.autoscaling.vpa.controlledResources`     | VPA List of resources that the vertical pod autoscaler can control. Defaults to cpu and memory                                                                         | `[]`    |
| `rootCoord.autoscaling.vpa.maxAllowed`              | VPA Max allowed resources for the pod                                                                                                                                  | `{}`    |
| `rootCoord.autoscaling.vpa.minAllowed`              | VPA Min allowed resources for the pod                                                                                                                                  | `{}`    |
| `rootCoord.autoscaling.vpa.updatePolicy.updateMode` | Autoscaling update policy Specifies whether recommended updates are applied when a Pod is started and whether recommended updates are applied during the life of a Pod | `Auto`  |
| `rootCoord.autoscaling.hpa.enabled`                 | Enable HPA for Milvus Data Plane                                                                                                                                       | `false` |
| `rootCoord.autoscaling.hpa.annotations`             | Annotations for HPA resource                                                                                                                                           | `{}`    |
| `rootCoord.autoscaling.hpa.minReplicas`             | Minimum number of Milvus Data Plane replicas                                                                                                                           | `""`    |
| `rootCoord.autoscaling.hpa.maxReplicas`             | Maximum number of Milvus Data Plane replicas                                                                                                                           | `""`    |
| `rootCoord.autoscaling.hpa.targetCPU`               | Target CPU utilization percentage                                                                                                                                      | `""`    |
| `rootCoord.autoscaling.hpa.targetMemory`            | Target Memory utilization percentage                                                                                                                                   | `""`    |

### Root Coordinator Traffic Exposure Parameters

| Name                                              | Description                                                      | Value       |
| ------------------------------------------------- | ---------------------------------------------------------------- | ----------- |
| `rootCoord.service.type`                          | Root Coordinator service type                                    | `ClusterIP` |
| `rootCoord.service.ports.grpc`                    | Root Coordinator GRPC service port                               | `19530`     |
| `rootCoord.service.ports.metrics`                 | Root Coordinator Metrics service port                            | `9091`      |
| `rootCoord.service.nodePorts.grpc`                | Node port for GRPC                                               | `""`        |
| `rootCoord.service.nodePorts.metrics`             | Node port for Metrics                                            | `""`        |
| `rootCoord.service.sessionAffinityConfig`         | Additional settings for the sessionAffinity                      | `{}`        |
| `rootCoord.service.sessionAffinity`               | Control where client requests go, to the same pod or round-robin | `None`      |
| `rootCoord.service.clusterIP`                     | Root Coordinator service Cluster IP                              | `""`        |
| `rootCoord.service.loadBalancerIP`                | Root Coordinator service Load Balancer IP                        | `""`        |
| `rootCoord.service.loadBalancerSourceRanges`      | Root Coordinator service Load Balancer sources                   | `[]`        |
| `rootCoord.service.externalTrafficPolicy`         | Root Coordinator service external traffic policy                 | `Cluster`   |
| `rootCoord.service.annotations`                   | Additional custom annotations for Root Coordinator service       | `{}`        |
| `rootCoord.service.extraPorts`                    | Extra ports to expose in the Root Coordinator service            | `[]`        |
| `rootCoord.networkPolicy.enabled`                 | Enable creation of NetworkPolicy resources                       | `false`     |
| `rootCoord.networkPolicy.allowExternal`           | The Policy model to apply                                        | `true`      |
| `rootCoord.networkPolicy.extraIngress`            | Add extra ingress rules to the NetworkPolicy                     | `[]`        |
| `rootCoord.networkPolicy.extraEgress`             | Add extra ingress rules to the NetworkPolicy                     | `[]`        |
| `rootCoord.networkPolicy.ingressNSMatchLabels`    | Labels to match to allow traffic from other namespaces           | `{}`        |
| `rootCoord.networkPolicy.ingressNSPodMatchLabels` | Pod labels to match to allow traffic from other namespaces       | `{}`        |

### Root Coordinator Metrics Parameters

| Name                                                 | Description                                                                           | Value   |
| ---------------------------------------------------- | ------------------------------------------------------------------------------------- | ------- |
| `rootCoord.metrics.enabled`                          | Enable metrics                                                                        | `false` |
| `rootCoord.metrics.annotations`                      | Annotations for the server service in order to scrape metrics                         | `{}`    |
| `rootCoord.metrics.serviceMonitor.enabled`           | Create ServiceMonitor Resource for scraping metrics using Prometheus Operator         | `false` |
| `rootCoord.metrics.serviceMonitor.annotations`       | Annotations for the ServiceMonitor Resource                                           | `""`    |
| `rootCoord.metrics.serviceMonitor.namespace`         | Namespace for the ServiceMonitor Resource (defaults to the Release Namespace)         | `""`    |
| `rootCoord.metrics.serviceMonitor.interval`          | Interval at which metrics should be scraped.                                          | `""`    |
| `rootCoord.metrics.serviceMonitor.scrapeTimeout`     | Timeout after which the scrape is ended                                               | `""`    |
| `rootCoord.metrics.serviceMonitor.labels`            | Additional labels that can be used so ServiceMonitor will be discovered by Prometheus | `{}`    |
| `rootCoord.metrics.serviceMonitor.selector`          | Prometheus instance selector labels                                                   | `{}`    |
| `rootCoord.metrics.serviceMonitor.relabelings`       | RelabelConfigs to apply to samples before scraping                                    | `[]`    |
| `rootCoord.metrics.serviceMonitor.metricRelabelings` | MetricRelabelConfigs to apply to samples before ingestion                             | `[]`    |
| `rootCoord.metrics.serviceMonitor.honorLabels`       | Specify honorLabels parameter to add the scrape endpoint                              | `false` |
| `rootCoord.metrics.serviceMonitor.jobLabel`          | The name of the label on the target service to use as the job name in prometheus.     | `""`    |

### Query Coordinator Deployment Parameters

| Name                                                           | Description                                                                                                | Value            |
| -------------------------------------------------------------- | ---------------------------------------------------------------------------------------------------------- | ---------------- |
| `queryCoord.enabled`                                           | Enable Query Coordinator deployment                                                                        | `true`           |
| `queryCoord.extraEnvVars`                                      | Array with extra environment variables to add to data coordinator nodes                                    | `[]`             |
| `queryCoord.extraEnvVarsCM`                                    | Name of existing ConfigMap containing extra env vars for data coordinator nodes                            | `""`             |
| `queryCoord.extraEnvVarsSecret`                                | Name of existing Secret containing extra env vars for data coordinator nodes                               | `""`             |
| `queryCoord.defaultConfig`                                     | Default override configuration from the common set in milvus.defaultConfig                                 | `""`             |
| `queryCoord.existingConfigMap`                                 | name of a ConfigMap with existing configuration for the default configuration                              | `""`             |
| `queryCoord.extraConfig`                                       | Override configuration                                                                                     | `{}`             |
| `queryCoord.extraConfigExistingConfigMap`                      | name of a ConfigMap with existing configuration for the Dashboard                                          | `""`             |
| `queryCoord.command`                                           | Override default container command (useful when using custom images)                                       | `[]`             |
| `queryCoord.args`                                              | Override default container args (useful when using custom images)                                          | `[]`             |
| `queryCoord.replicaCount`                                      | Number of Query Coordinator replicas to deploy                                                             | `1`              |
| `queryCoord.containerPorts.grpc`                               | GRPC port for Query Coordinator                                                                            | `19530`          |
| `queryCoord.containerPorts.metrics`                            | Metrics port for Query Coordinator                                                                         | `9091`           |
| `queryCoord.livenessProbe.enabled`                             | Enable livenessProbe on Query Coordinator nodes                                                            | `true`           |
| `queryCoord.livenessProbe.initialDelaySeconds`                 | Initial delay seconds for livenessProbe                                                                    | `5`              |
| `queryCoord.livenessProbe.periodSeconds`                       | Period seconds for livenessProbe                                                                           | `10`             |
| `queryCoord.livenessProbe.timeoutSeconds`                      | Timeout seconds for livenessProbe                                                                          | `5`              |
| `queryCoord.livenessProbe.failureThreshold`                    | Failure threshold for livenessProbe                                                                        | `5`              |
| `queryCoord.livenessProbe.successThreshold`                    | Success threshold for livenessProbe                                                                        | `1`              |
| `queryCoord.readinessProbe.enabled`                            | Enable readinessProbe on Query Coordinator nodes                                                           | `true`           |
| `queryCoord.readinessProbe.initialDelaySeconds`                | Initial delay seconds for readinessProbe                                                                   | `5`              |
| `queryCoord.readinessProbe.periodSeconds`                      | Period seconds for readinessProbe                                                                          | `10`             |
| `queryCoord.readinessProbe.timeoutSeconds`                     | Timeout seconds for readinessProbe                                                                         | `5`              |
| `queryCoord.readinessProbe.failureThreshold`                   | Failure threshold for readinessProbe                                                                       | `5`              |
| `queryCoord.readinessProbe.successThreshold`                   | Success threshold for readinessProbe                                                                       | `1`              |
| `queryCoord.startupProbe.enabled`                              | Enable startupProbe on Query Coordinator containers                                                        | `false`          |
| `queryCoord.startupProbe.initialDelaySeconds`                  | Initial delay seconds for startupProbe                                                                     | `5`              |
| `queryCoord.startupProbe.periodSeconds`                        | Period seconds for startupProbe                                                                            | `10`             |
| `queryCoord.startupProbe.timeoutSeconds`                       | Timeout seconds for startupProbe                                                                           | `5`              |
| `queryCoord.startupProbe.failureThreshold`                     | Failure threshold for startupProbe                                                                         | `5`              |
| `queryCoord.startupProbe.successThreshold`                     | Success threshold for startupProbe                                                                         | `1`              |
| `queryCoord.customLivenessProbe`                               | Custom livenessProbe that overrides the default one                                                        | `{}`             |
| `queryCoord.customReadinessProbe`                              | Custom readinessProbe that overrides the default one                                                       | `{}`             |
| `queryCoord.customStartupProbe`                                | Custom startupProbe that overrides the default one                                                         | `{}`             |
| `queryCoord.resources.limits`                                  | The resources limits for the data coordinator containers                                                   | `{}`             |
| `queryCoord.resources.requests`                                | The requested resources for the data coordinator containers                                                | `{}`             |
| `queryCoord.podSecurityContext.enabled`                        | Enabled Query Coordinator pods' Security Context                                                           | `true`           |
| `queryCoord.podSecurityContext.fsGroup`                        | Set Query Coordinator pod's Security Context fsGroup                                                       | `1001`           |
| `queryCoord.containerSecurityContext.enabled`                  | Enabled containers' Security Context                                                                       | `true`           |
| `queryCoord.containerSecurityContext.runAsUser`                | Set containers' Security Context runAsUser                                                                 | `1001`           |
| `queryCoord.containerSecurityContext.runAsNonRoot`             | Set container's Security Context runAsNonRoot                                                              | `true`           |
| `queryCoord.containerSecurityContext.privileged`               | Set container's Security Context privileged                                                                | `false`          |
| `queryCoord.containerSecurityContext.readOnlyRootFilesystem`   | Set container's Security Context readOnlyRootFilesystem                                                    | `true`           |
| `queryCoord.containerSecurityContext.allowPrivilegeEscalation` | Set container's Security Context allowPrivilegeEscalation                                                  | `false`          |
| `queryCoord.containerSecurityContext.capabilities.drop`        | List of capabilities to be dropped                                                                         | `["ALL"]`        |
| `queryCoord.containerSecurityContext.seccompProfile.type`      | Set container's Security Context seccomp profile                                                           | `RuntimeDefault` |
| `queryCoord.lifecycleHooks`                                    | for the data coordinator container(s) to automate configuration before or after startup                    | `{}`             |
| `queryCoord.runtimeClassName`                                  | Name of the runtime class to be used by pod(s)                                                             | `""`             |
| `queryCoord.hostAliases`                                       | data coordinator pods host aliases                                                                         | `[]`             |
| `queryCoord.podLabels`                                         | Extra labels for data coordinator pods                                                                     | `{}`             |
| `queryCoord.podAnnotations`                                    | Annotations for data coordinator pods                                                                      | `{}`             |
| `queryCoord.podAffinityPreset`                                 | Pod affinity preset. Ignored if `data coordinator.affinity` is set. Allowed values: `soft` or `hard`       | `""`             |
| `queryCoord.podAntiAffinityPreset`                             | Pod anti-affinity preset. Ignored if `data coordinator.affinity` is set. Allowed values: `soft` or `hard`  | `soft`           |
| `queryCoord.nodeAffinityPreset.type`                           | Node affinity preset type. Ignored if `data coordinator.affinity` is set. Allowed values: `soft` or `hard` | `""`             |
| `queryCoord.nodeAffinityPreset.key`                            | Node label key to match. Ignored if `data coordinator.affinity` is set                                     | `""`             |
| `queryCoord.nodeAffinityPreset.values`                         | Node label values to match. Ignored if `data coordinator.affinity` is set                                  | `[]`             |
| `queryCoord.affinity`                                          | Affinity for Query Coordinator pods assignment                                                             | `{}`             |
| `queryCoord.nodeSelector`                                      | Node labels for Query Coordinator pods assignment                                                          | `{}`             |
| `queryCoord.tolerations`                                       | Tolerations for Query Coordinator pods assignment                                                          | `[]`             |
| `queryCoord.topologySpreadConstraints`                         | Topology Spread Constraints for pod assignment spread across your cluster among failure-domains            | `[]`             |
| `queryCoord.priorityClassName`                                 | Query Coordinator pods' priorityClassName                                                                  | `""`             |
| `queryCoord.schedulerName`                                     | Kubernetes pod scheduler registry                                                                          | `""`             |
| `queryCoord.updateStrategy.type`                               | Query Coordinator statefulset strategy type                                                                | `RollingUpdate`  |
| `queryCoord.updateStrategy.rollingUpdate`                      | Query Coordinator statefulset rolling update configuration parameters                                      | `{}`             |
| `queryCoord.extraVolumes`                                      | Optionally specify extra list of additional volumes for the Query Coordinator pod(s)                       | `[]`             |
| `queryCoord.extraVolumeMounts`                                 | Optionally specify extra list of additional volumeMounts for the Query Coordinator container(s)            | `[]`             |
| `queryCoord.sidecars`                                          | Add additional sidecar containers to the Query Coordinator pod(s)                                          | `[]`             |
| `queryCoord.enableDefaultInitContainers`                       | Deploy default init containers                                                                             | `true`           |
| `queryCoord.initContainers`                                    | Add additional init containers to the Query Coordinator pod(s)                                             | `[]`             |
| `queryCoord.serviceAccount.create`                             | Enable creation of ServiceAccount for Query Coordinator pods                                               | `false`          |
| `queryCoord.serviceAccount.name`                               | The name of the ServiceAccount to use                                                                      | `""`             |
| `queryCoord.serviceAccount.automountServiceAccountToken`       | Allows auto mount of ServiceAccountToken on the serviceAccount created                                     | `false`          |
| `queryCoord.serviceAccount.annotations`                        | Additional custom annotations for the ServiceAccount                                                       | `{}`             |
| `queryCoord.pdb.create`                                        | Enable/disable a Pod Disruption Budget creation                                                            | `false`          |
| `queryCoord.pdb.minAvailable`                                  | Minimum number/percentage of pods that should remain scheduled                                             | `1`              |
| `queryCoord.pdb.maxUnavailable`                                | Maximum number/percentage of pods that may be made unavailable                                             | `""`             |

### Query Coordinator Autoscaling configuration

| Name                                                 | Description                                                                                                                                                            | Value   |
| ---------------------------------------------------- | ---------------------------------------------------------------------------------------------------------------------------------------------------------------------- | ------- |
| `queryCoord.autoscaling.vpa.enabled`                 | Enable VPA                                                                                                                                                             | `false` |
| `queryCoord.autoscaling.vpa.annotations`             | Annotations for VPA resource                                                                                                                                           | `{}`    |
| `queryCoord.autoscaling.vpa.controlledResources`     | VPA List of resources that the vertical pod autoscaler can control. Defaults to cpu and memory                                                                         | `[]`    |
| `queryCoord.autoscaling.vpa.maxAllowed`              | VPA Max allowed resources for the pod                                                                                                                                  | `{}`    |
| `queryCoord.autoscaling.vpa.minAllowed`              | VPA Min allowed resources for the pod                                                                                                                                  | `{}`    |
| `queryCoord.autoscaling.vpa.updatePolicy.updateMode` | Autoscaling update policy Specifies whether recommended updates are applied when a Pod is started and whether recommended updates are applied during the life of a Pod | `Auto`  |
| `queryCoord.autoscaling.hpa.enabled`                 | Enable HPA for Milvus Data Plane                                                                                                                                       | `false` |
| `queryCoord.autoscaling.hpa.annotations`             | Annotations for HPA resource                                                                                                                                           | `{}`    |
| `queryCoord.autoscaling.hpa.minReplicas`             | Minimum number of Milvus Data Plane replicas                                                                                                                           | `""`    |
| `queryCoord.autoscaling.hpa.maxReplicas`             | Maximum number of Milvus Data Plane replicas                                                                                                                           | `""`    |
| `queryCoord.autoscaling.hpa.targetCPU`               | Target CPU utilization percentage                                                                                                                                      | `""`    |
| `queryCoord.autoscaling.hpa.targetMemory`            | Target Memory utilization percentage                                                                                                                                   | `""`    |

### Query Coordinator Traffic Exposure Parameters

| Name                                               | Description                                                      | Value       |
| -------------------------------------------------- | ---------------------------------------------------------------- | ----------- |
| `queryCoord.service.type`                          | Query Coordinator service type                                   | `ClusterIP` |
| `queryCoord.service.ports.grpc`                    | Query Coordinator GRPC service port                              | `19530`     |
| `queryCoord.service.ports.metrics`                 | Query Coordinator Metrics service port                           | `9091`      |
| `queryCoord.service.nodePorts.grpc`                | Node port for GRPC                                               | `""`        |
| `queryCoord.service.nodePorts.metrics`             | Node port for Metrics                                            | `""`        |
| `queryCoord.service.sessionAffinityConfig`         | Additional settings for the sessionAffinity                      | `{}`        |
| `queryCoord.service.sessionAffinity`               | Control where client requests go, to the same pod or round-robin | `None`      |
| `queryCoord.service.clusterIP`                     | Query Coordinator service Cluster IP                             | `""`        |
| `queryCoord.service.loadBalancerIP`                | Query Coordinator service Load Balancer IP                       | `""`        |
| `queryCoord.service.loadBalancerSourceRanges`      | Query Coordinator service Load Balancer sources                  | `[]`        |
| `queryCoord.service.externalTrafficPolicy`         | Query Coordinator service external traffic policy                | `Cluster`   |
| `queryCoord.service.annotations`                   | Additional custom annotations for Query Coordinator service      | `{}`        |
| `queryCoord.service.extraPorts`                    | Extra ports to expose in the Query Coordinator service           | `[]`        |
| `queryCoord.networkPolicy.enabled`                 | Enable creation of NetworkPolicy resources                       | `false`     |
| `queryCoord.networkPolicy.allowExternal`           | The Policy model to apply                                        | `true`      |
| `queryCoord.networkPolicy.extraIngress`            | Add extra ingress rules to the NetworkPolicy                     | `[]`        |
| `queryCoord.networkPolicy.extraEgress`             | Add extra ingress rules to the NetworkPolicy                     | `[]`        |
| `queryCoord.networkPolicy.ingressNSMatchLabels`    | Labels to match to allow traffic from other namespaces           | `{}`        |
| `queryCoord.networkPolicy.ingressNSPodMatchLabels` | Pod labels to match to allow traffic from other namespaces       | `{}`        |

### Query Coordinator Metrics Parameters

| Name                                                  | Description                                                                           | Value   |
| ----------------------------------------------------- | ------------------------------------------------------------------------------------- | ------- |
| `queryCoord.metrics.enabled`                          | Enable metrics                                                                        | `false` |
| `queryCoord.metrics.annotations`                      | Annotations for the server service in order to scrape metrics                         | `{}`    |
| `queryCoord.metrics.serviceMonitor.enabled`           | Create ServiceMonitor Resource for scraping metrics using Prometheus Operator         | `false` |
| `queryCoord.metrics.serviceMonitor.annotations`       | Annotations for the ServiceMonitor Resource                                           | `""`    |
| `queryCoord.metrics.serviceMonitor.namespace`         | Namespace for the ServiceMonitor Resource (defaults to the Release Namespace)         | `""`    |
| `queryCoord.metrics.serviceMonitor.interval`          | Interval at which metrics should be scraped.                                          | `""`    |
| `queryCoord.metrics.serviceMonitor.scrapeTimeout`     | Timeout after which the scrape is ended                                               | `""`    |
| `queryCoord.metrics.serviceMonitor.labels`            | Additional labels that can be used so ServiceMonitor will be discovered by Prometheus | `{}`    |
| `queryCoord.metrics.serviceMonitor.selector`          | Prometheus instance selector labels                                                   | `{}`    |
| `queryCoord.metrics.serviceMonitor.relabelings`       | RelabelConfigs to apply to samples before scraping                                    | `[]`    |
| `queryCoord.metrics.serviceMonitor.metricRelabelings` | MetricRelabelConfigs to apply to samples before ingestion                             | `[]`    |
| `queryCoord.metrics.serviceMonitor.honorLabels`       | Specify honorLabels parameter to add the scrape endpoint                              | `false` |
| `queryCoord.metrics.serviceMonitor.jobLabel`          | The name of the label on the target service to use as the job name in prometheus.     | `""`    |

### Index Coordinator Deployment Parameters

| Name                                                           | Description                                                                                                | Value            |
| -------------------------------------------------------------- | ---------------------------------------------------------------------------------------------------------- | ---------------- |
| `indexCoord.enabled`                                           | Enable Index Coordinator deployment                                                                        | `true`           |
| `indexCoord.extraEnvVars`                                      | Array with extra environment variables to add to data coordinator nodes                                    | `[]`             |
| `indexCoord.extraEnvVarsCM`                                    | Name of existing ConfigMap containing extra env vars for data coordinator nodes                            | `""`             |
| `indexCoord.extraEnvVarsSecret`                                | Name of existing Secret containing extra env vars for data coordinator nodes                               | `""`             |
| `indexCoord.defaultConfig`                                     | Default override configuration from the common set in milvus.defaultConfig                                 | `""`             |
| `indexCoord.existingConfigMap`                                 | name of a ConfigMap with existing configuration for the default configuration                              | `""`             |
| `indexCoord.extraConfig`                                       | Override configuration                                                                                     | `{}`             |
| `indexCoord.extraConfigExistingConfigMap`                      | name of a ConfigMap with existing configuration for the Dashboard                                          | `""`             |
| `indexCoord.command`                                           | Override default container command (useful when using custom images)                                       | `[]`             |
| `indexCoord.args`                                              | Override default container args (useful when using custom images)                                          | `[]`             |
| `indexCoord.replicaCount`                                      | Number of Index Coordinator replicas to deploy                                                             | `1`              |
| `indexCoord.containerPorts.grpc`                               | GRPC port for Index Coordinator                                                                            | `19530`          |
| `indexCoord.containerPorts.metrics`                            | Metrics port for Index Coordinator                                                                         | `9091`           |
| `indexCoord.livenessProbe.enabled`                             | Enable livenessProbe on Index Coordinator nodes                                                            | `true`           |
| `indexCoord.livenessProbe.initialDelaySeconds`                 | Initial delay seconds for livenessProbe                                                                    | `5`              |
| `indexCoord.livenessProbe.periodSeconds`                       | Period seconds for livenessProbe                                                                           | `10`             |
| `indexCoord.livenessProbe.timeoutSeconds`                      | Timeout seconds for livenessProbe                                                                          | `5`              |
| `indexCoord.livenessProbe.failureThreshold`                    | Failure threshold for livenessProbe                                                                        | `5`              |
| `indexCoord.livenessProbe.successThreshold`                    | Success threshold for livenessProbe                                                                        | `1`              |
| `indexCoord.readinessProbe.enabled`                            | Enable readinessProbe on Index Coordinator nodes                                                           | `true`           |
| `indexCoord.readinessProbe.initialDelaySeconds`                | Initial delay seconds for readinessProbe                                                                   | `5`              |
| `indexCoord.readinessProbe.periodSeconds`                      | Period seconds for readinessProbe                                                                          | `10`             |
| `indexCoord.readinessProbe.timeoutSeconds`                     | Timeout seconds for readinessProbe                                                                         | `5`              |
| `indexCoord.readinessProbe.failureThreshold`                   | Failure threshold for readinessProbe                                                                       | `5`              |
| `indexCoord.readinessProbe.successThreshold`                   | Success threshold for readinessProbe                                                                       | `1`              |
| `indexCoord.startupProbe.enabled`                              | Enable startupProbe on Index Coordinator containers                                                        | `false`          |
| `indexCoord.startupProbe.initialDelaySeconds`                  | Initial delay seconds for startupProbe                                                                     | `5`              |
| `indexCoord.startupProbe.periodSeconds`                        | Period seconds for startupProbe                                                                            | `10`             |
| `indexCoord.startupProbe.timeoutSeconds`                       | Timeout seconds for startupProbe                                                                           | `5`              |
| `indexCoord.startupProbe.failureThreshold`                     | Failure threshold for startupProbe                                                                         | `5`              |
| `indexCoord.startupProbe.successThreshold`                     | Success threshold for startupProbe                                                                         | `1`              |
| `indexCoord.customLivenessProbe`                               | Custom livenessProbe that overrides the default one                                                        | `{}`             |
| `indexCoord.customReadinessProbe`                              | Custom readinessProbe that overrides the default one                                                       | `{}`             |
| `indexCoord.customStartupProbe`                                | Custom startupProbe that overrides the default one                                                         | `{}`             |
| `indexCoord.resources.limits`                                  | The resources limits for the data coordinator containers                                                   | `{}`             |
| `indexCoord.resources.requests`                                | The requested resources for the data coordinator containers                                                | `{}`             |
| `indexCoord.podSecurityContext.enabled`                        | Enabled Index Coordinator pods' Security Context                                                           | `true`           |
| `indexCoord.podSecurityContext.fsGroup`                        | Set Index Coordinator pod's Security Context fsGroup                                                       | `1001`           |
| `indexCoord.containerSecurityContext.enabled`                  | Enabled containers' Security Context                                                                       | `true`           |
| `indexCoord.containerSecurityContext.runAsUser`                | Set containers' Security Context runAsUser                                                                 | `1001`           |
| `indexCoord.containerSecurityContext.runAsNonRoot`             | Set container's Security Context runAsNonRoot                                                              | `true`           |
| `indexCoord.containerSecurityContext.privileged`               | Set container's Security Context privileged                                                                | `false`          |
| `indexCoord.containerSecurityContext.readOnlyRootFilesystem`   | Set container's Security Context readOnlyRootFilesystem                                                    | `true`           |
| `indexCoord.containerSecurityContext.allowPrivilegeEscalation` | Set container's Security Context allowPrivilegeEscalation                                                  | `false`          |
| `indexCoord.containerSecurityContext.capabilities.drop`        | List of capabilities to be dropped                                                                         | `["ALL"]`        |
| `indexCoord.containerSecurityContext.seccompProfile.type`      | Set container's Security Context seccomp profile                                                           | `RuntimeDefault` |
| `indexCoord.lifecycleHooks`                                    | for the data coordinator container(s) to automate configuration before or after startup                    | `{}`             |
| `indexCoord.runtimeClassName`                                  | Name of the runtime class to be used by pod(s)                                                             | `""`             |
| `indexCoord.hostAliases`                                       | data coordinator pods host aliases                                                                         | `[]`             |
| `indexCoord.podLabels`                                         | Extra labels for data coordinator pods                                                                     | `{}`             |
| `indexCoord.podAnnotations`                                    | Annotations for data coordinator pods                                                                      | `{}`             |
| `indexCoord.podAffinityPreset`                                 | Pod affinity preset. Ignored if `data coordinator.affinity` is set. Allowed values: `soft` or `hard`       | `""`             |
| `indexCoord.podAntiAffinityPreset`                             | Pod anti-affinity preset. Ignored if `data coordinator.affinity` is set. Allowed values: `soft` or `hard`  | `soft`           |
| `indexCoord.nodeAffinityPreset.type`                           | Node affinity preset type. Ignored if `data coordinator.affinity` is set. Allowed values: `soft` or `hard` | `""`             |
| `indexCoord.nodeAffinityPreset.key`                            | Node label key to match. Ignored if `data coordinator.affinity` is set                                     | `""`             |
| `indexCoord.nodeAffinityPreset.values`                         | Node label values to match. Ignored if `data coordinator.affinity` is set                                  | `[]`             |
| `indexCoord.affinity`                                          | Affinity for Index Coordinator pods assignment                                                             | `{}`             |
| `indexCoord.nodeSelector`                                      | Node labels for Index Coordinator pods assignment                                                          | `{}`             |
| `indexCoord.tolerations`                                       | Tolerations for Index Coordinator pods assignment                                                          | `[]`             |
| `indexCoord.topologySpreadConstraints`                         | Topology Spread Constraints for pod assignment spread across your cluster among failure-domains            | `[]`             |
| `indexCoord.priorityClassName`                                 | Index Coordinator pods' priorityClassName                                                                  | `""`             |
| `indexCoord.schedulerName`                                     | Kubernetes pod scheduler registry                                                                          | `""`             |
| `indexCoord.updateStrategy.type`                               | Index Coordinator statefulset strategy type                                                                | `RollingUpdate`  |
| `indexCoord.updateStrategy.rollingUpdate`                      | Index Coordinator statefulset rolling update configuration parameters                                      | `{}`             |
| `indexCoord.extraVolumes`                                      | Optionally specify extra list of additional volumes for the Index Coordinator pod(s)                       | `[]`             |
| `indexCoord.extraVolumeMounts`                                 | Optionally specify extra list of additional volumeMounts for the Index Coordinator container(s)            | `[]`             |
| `indexCoord.sidecars`                                          | Add additional sidecar containers to the Index Coordinator pod(s)                                          | `[]`             |
| `indexCoord.enableDefaultInitContainers`                       | Deploy default init containers                                                                             | `true`           |
| `indexCoord.initContainers`                                    | Add additional init containers to the Index Coordinator pod(s)                                             | `[]`             |
| `indexCoord.serviceAccount.create`                             | Enable creation of ServiceAccount for Index Coordinator pods                                               | `false`          |
| `indexCoord.serviceAccount.name`                               | The name of the ServiceAccount to use                                                                      | `""`             |
| `indexCoord.serviceAccount.automountServiceAccountToken`       | Allows auto mount of ServiceAccountToken on the serviceAccount created                                     | `false`          |
| `indexCoord.serviceAccount.annotations`                        | Additional custom annotations for the ServiceAccount                                                       | `{}`             |
| `indexCoord.pdb.create`                                        | Enable/disable a Pod Disruption Budget creation                                                            | `false`          |
| `indexCoord.pdb.minAvailable`                                  | Minimum number/percentage of pods that should remain scheduled                                             | `1`              |
| `indexCoord.pdb.maxUnavailable`                                | Maximum number/percentage of pods that may be made unavailable                                             | `""`             |

### Index Coordinator Autoscaling configuration

| Name                                                 | Description                                                                                                                                                            | Value   |
| ---------------------------------------------------- | ---------------------------------------------------------------------------------------------------------------------------------------------------------------------- | ------- |
| `indexCoord.autoscaling.vpa.enabled`                 | Enable VPA                                                                                                                                                             | `false` |
| `indexCoord.autoscaling.vpa.annotations`             | Annotations for VPA resource                                                                                                                                           | `{}`    |
| `indexCoord.autoscaling.vpa.controlledResources`     | VPA List of resources that the vertical pod autoscaler can control. Defaults to cpu and memory                                                                         | `[]`    |
| `indexCoord.autoscaling.vpa.maxAllowed`              | VPA Max allowed resources for the pod                                                                                                                                  | `{}`    |
| `indexCoord.autoscaling.vpa.minAllowed`              | VPA Min allowed resources for the pod                                                                                                                                  | `{}`    |
| `indexCoord.autoscaling.vpa.updatePolicy.updateMode` | Autoscaling update policy Specifies whether recommended updates are applied when a Pod is started and whether recommended updates are applied during the life of a Pod | `Auto`  |
| `indexCoord.autoscaling.hpa.enabled`                 | Enable HPA for Milvus Data Plane                                                                                                                                       | `false` |
| `indexCoord.autoscaling.hpa.annotations`             | Annotations for HPA resource                                                                                                                                           | `{}`    |
| `indexCoord.autoscaling.hpa.minReplicas`             | Minimum number of Milvus Data Plane replicas                                                                                                                           | `""`    |
| `indexCoord.autoscaling.hpa.maxReplicas`             | Maximum number of Milvus Data Plane replicas                                                                                                                           | `""`    |
| `indexCoord.autoscaling.hpa.targetCPU`               | Target CPU utilization percentage                                                                                                                                      | `""`    |
| `indexCoord.autoscaling.hpa.targetMemory`            | Target Memory utilization percentage                                                                                                                                   | `""`    |

### Index Coordinator Traffic Exposure Parameters

| Name                                               | Description                                                      | Value       |
| -------------------------------------------------- | ---------------------------------------------------------------- | ----------- |
| `indexCoord.service.type`                          | Index Coordinator service type                                   | `ClusterIP` |
| `indexCoord.service.ports.grpc`                    | Index Coordinator GRPC service port                              | `19530`     |
| `indexCoord.service.ports.metrics`                 | Index Coordinator Metrics service port                           | `9091`      |
| `indexCoord.service.nodePorts.grpc`                | Node port for GRPC                                               | `""`        |
| `indexCoord.service.nodePorts.metrics`             | Node port for Metrics                                            | `""`        |
| `indexCoord.service.sessionAffinityConfig`         | Additional settings for the sessionAffinity                      | `{}`        |
| `indexCoord.service.sessionAffinity`               | Control where client requests go, to the same pod or round-robin | `None`      |
| `indexCoord.service.clusterIP`                     | Index Coordinator service Cluster IP                             | `""`        |
| `indexCoord.service.loadBalancerIP`                | Index Coordinator service Load Balancer IP                       | `""`        |
| `indexCoord.service.loadBalancerSourceRanges`      | Index Coordinator service Load Balancer sources                  | `[]`        |
| `indexCoord.service.externalTrafficPolicy`         | Index Coordinator service external traffic policy                | `Cluster`   |
| `indexCoord.service.annotations`                   | Additional custom annotations for Index Coordinator service      | `{}`        |
| `indexCoord.service.extraPorts`                    | Extra ports to expose in the Index Coordinator service           | `[]`        |
| `indexCoord.networkPolicy.enabled`                 | Enable creation of NetworkPolicy resources                       | `false`     |
| `indexCoord.networkPolicy.allowExternal`           | The Policy model to apply                                        | `true`      |
| `indexCoord.networkPolicy.extraIngress`            | Add extra ingress rules to the NetworkPolicy                     | `[]`        |
| `indexCoord.networkPolicy.extraEgress`             | Add extra ingress rules to the NetworkPolicy                     | `[]`        |
| `indexCoord.networkPolicy.ingressNSMatchLabels`    | Labels to match to allow traffic from other namespaces           | `{}`        |
| `indexCoord.networkPolicy.ingressNSPodMatchLabels` | Pod labels to match to allow traffic from other namespaces       | `{}`        |

### Index Coordinator Metrics Parameters

| Name                                                  | Description                                                                           | Value   |
| ----------------------------------------------------- | ------------------------------------------------------------------------------------- | ------- |
| `indexCoord.metrics.enabled`                          | Enable metrics                                                                        | `false` |
| `indexCoord.metrics.annotations`                      | Annotations for the server service in order to scrape metrics                         | `{}`    |
| `indexCoord.metrics.serviceMonitor.enabled`           | Create ServiceMonitor Resource for scraping metrics using Prometheus Operator         | `false` |
| `indexCoord.metrics.serviceMonitor.annotations`       | Annotations for the ServiceMonitor Resource                                           | `""`    |
| `indexCoord.metrics.serviceMonitor.namespace`         | Namespace for the ServiceMonitor Resource (defaults to the Release Namespace)         | `""`    |
| `indexCoord.metrics.serviceMonitor.interval`          | Interval at which metrics should be scraped.                                          | `""`    |
| `indexCoord.metrics.serviceMonitor.scrapeTimeout`     | Timeout after which the scrape is ended                                               | `""`    |
| `indexCoord.metrics.serviceMonitor.labels`            | Additional labels that can be used so ServiceMonitor will be discovered by Prometheus | `{}`    |
| `indexCoord.metrics.serviceMonitor.selector`          | Prometheus instance selector labels                                                   | `{}`    |
| `indexCoord.metrics.serviceMonitor.relabelings`       | RelabelConfigs to apply to samples before scraping                                    | `[]`    |
| `indexCoord.metrics.serviceMonitor.metricRelabelings` | MetricRelabelConfigs to apply to samples before ingestion                             | `[]`    |
| `indexCoord.metrics.serviceMonitor.honorLabels`       | Specify honorLabels parameter to add the scrape endpoint                              | `false` |
| `indexCoord.metrics.serviceMonitor.jobLabel`          | The name of the label on the target service to use as the job name in prometheus.     | `""`    |

### Data Node Deployment Parameters

| Name                                                         | Description                                                                                         | Value            |
| ------------------------------------------------------------ | --------------------------------------------------------------------------------------------------- | ---------------- |
| `dataNode.enabled`                                           | Enable Data Node deployment                                                                         | `true`           |
| `dataNode.extraEnvVars`                                      | Array with extra environment variables to add to data node nodes                                    | `[]`             |
| `dataNode.extraEnvVarsCM`                                    | Name of existing ConfigMap containing extra env vars for data node nodes                            | `""`             |
| `dataNode.extraEnvVarsSecret`                                | Name of existing Secret containing extra env vars for data node nodes                               | `""`             |
| `dataNode.defaultConfig`                                     | Default override configuration from the common set in milvus.defaultConfig                          | `""`             |
| `dataNode.existingConfigMap`                                 | name of a ConfigMap with existing configuration for the default configuration                       | `""`             |
| `dataNode.extraConfig`                                       | Override configuration                                                                              | `{}`             |
| `dataNode.extraConfigExistingConfigMap`                      | name of a ConfigMap with existing configuration for the Dashboard                                   | `""`             |
| `dataNode.command`                                           | Override default container command (useful when using custom images)                                | `[]`             |
| `dataNode.args`                                              | Override default container args (useful when using custom images)                                   | `[]`             |
| `dataNode.replicaCount`                                      | Number of Data Node replicas to deploy                                                              | `1`              |
| `dataNode.containerPorts.grpc`                               | GRPC port for Data Node                                                                             | `19530`          |
| `dataNode.containerPorts.metrics`                            | Metrics port for Data Node                                                                          | `9091`           |
| `dataNode.livenessProbe.enabled`                             | Enable livenessProbe on Data Node nodes                                                             | `true`           |
| `dataNode.livenessProbe.initialDelaySeconds`                 | Initial delay seconds for livenessProbe                                                             | `5`              |
| `dataNode.livenessProbe.periodSeconds`                       | Period seconds for livenessProbe                                                                    | `10`             |
| `dataNode.livenessProbe.timeoutSeconds`                      | Timeout seconds for livenessProbe                                                                   | `5`              |
| `dataNode.livenessProbe.failureThreshold`                    | Failure threshold for livenessProbe                                                                 | `5`              |
| `dataNode.livenessProbe.successThreshold`                    | Success threshold for livenessProbe                                                                 | `1`              |
| `dataNode.readinessProbe.enabled`                            | Enable readinessProbe on Data Node nodes                                                            | `true`           |
| `dataNode.readinessProbe.initialDelaySeconds`                | Initial delay seconds for readinessProbe                                                            | `5`              |
| `dataNode.readinessProbe.periodSeconds`                      | Period seconds for readinessProbe                                                                   | `10`             |
| `dataNode.readinessProbe.timeoutSeconds`                     | Timeout seconds for readinessProbe                                                                  | `5`              |
| `dataNode.readinessProbe.failureThreshold`                   | Failure threshold for readinessProbe                                                                | `5`              |
| `dataNode.readinessProbe.successThreshold`                   | Success threshold for readinessProbe                                                                | `1`              |
| `dataNode.startupProbe.enabled`                              | Enable startupProbe on Data Node containers                                                         | `false`          |
| `dataNode.startupProbe.initialDelaySeconds`                  | Initial delay seconds for startupProbe                                                              | `5`              |
| `dataNode.startupProbe.periodSeconds`                        | Period seconds for startupProbe                                                                     | `10`             |
| `dataNode.startupProbe.timeoutSeconds`                       | Timeout seconds for startupProbe                                                                    | `5`              |
| `dataNode.startupProbe.failureThreshold`                     | Failure threshold for startupProbe                                                                  | `5`              |
| `dataNode.startupProbe.successThreshold`                     | Success threshold for startupProbe                                                                  | `1`              |
| `dataNode.customLivenessProbe`                               | Custom livenessProbe that overrides the default one                                                 | `{}`             |
| `dataNode.customReadinessProbe`                              | Custom readinessProbe that overrides the default one                                                | `{}`             |
| `dataNode.customStartupProbe`                                | Custom startupProbe that overrides the default one                                                  | `{}`             |
| `dataNode.resources.limits`                                  | The resources limits for the data node containers                                                   | `{}`             |
| `dataNode.resources.requests`                                | The requested resources for the data node containers                                                | `{}`             |
| `dataNode.podSecurityContext.enabled`                        | Enabled Data Node pods' Security Context                                                            | `true`           |
| `dataNode.podSecurityContext.fsGroup`                        | Set Data Node pod's Security Context fsGroup                                                        | `1001`           |
| `dataNode.containerSecurityContext.enabled`                  | Enabled containers' Security Context                                                                | `true`           |
| `dataNode.containerSecurityContext.runAsUser`                | Set containers' Security Context runAsUser                                                          | `1001`           |
| `dataNode.containerSecurityContext.runAsNonRoot`             | Set container's Security Context runAsNonRoot                                                       | `true`           |
| `dataNode.containerSecurityContext.privileged`               | Set container's Security Context privileged                                                         | `false`          |
| `dataNode.containerSecurityContext.readOnlyRootFilesystem`   | Set container's Security Context readOnlyRootFilesystem                                             | `true`           |
| `dataNode.containerSecurityContext.allowPrivilegeEscalation` | Set container's Security Context allowPrivilegeEscalation                                           | `false`          |
| `dataNode.containerSecurityContext.capabilities.drop`        | List of capabilities to be dropped                                                                  | `["ALL"]`        |
| `dataNode.containerSecurityContext.seccompProfile.type`      | Set container's Security Context seccomp profile                                                    | `RuntimeDefault` |
| `dataNode.lifecycleHooks`                                    | for the data node container(s) to automate configuration before or after startup                    | `{}`             |
| `dataNode.runtimeClassName`                                  | Name of the runtime class to be used by pod(s)                                                      | `""`             |
| `dataNode.hostAliases`                                       | data node pods host aliases                                                                         | `[]`             |
| `dataNode.podLabels`                                         | Extra labels for data node pods                                                                     | `{}`             |
| `dataNode.podAnnotations`                                    | Annotations for data node pods                                                                      | `{}`             |
| `dataNode.podAffinityPreset`                                 | Pod affinity preset. Ignored if `data node.affinity` is set. Allowed values: `soft` or `hard`       | `""`             |
| `dataNode.podAntiAffinityPreset`                             | Pod anti-affinity preset. Ignored if `data node.affinity` is set. Allowed values: `soft` or `hard`  | `soft`           |
| `dataNode.nodeAffinityPreset.type`                           | Node affinity preset type. Ignored if `data node.affinity` is set. Allowed values: `soft` or `hard` | `""`             |
| `dataNode.nodeAffinityPreset.key`                            | Node label key to match. Ignored if `data node.affinity` is set                                     | `""`             |
| `dataNode.nodeAffinityPreset.values`                         | Node label values to match. Ignored if `data node.affinity` is set                                  | `[]`             |
| `dataNode.affinity`                                          | Affinity for Data Node pods assignment                                                              | `{}`             |
| `dataNode.nodeSelector`                                      | Node labels for Data Node pods assignment                                                           | `{}`             |
| `dataNode.tolerations`                                       | Tolerations for Data Node pods assignment                                                           | `[]`             |
| `dataNode.topologySpreadConstraints`                         | Topology Spread Constraints for pod assignment spread across your cluster among failure-domains     | `[]`             |
| `dataNode.priorityClassName`                                 | Data Node pods' priorityClassName                                                                   | `""`             |
| `dataNode.schedulerName`                                     | Kubernetes pod scheduler registry                                                                   | `""`             |
| `dataNode.updateStrategy.type`                               | Data Node statefulset strategy type                                                                 | `RollingUpdate`  |
| `dataNode.updateStrategy.rollingUpdate`                      | Data Node statefulset rolling update configuration parameters                                       | `{}`             |
| `dataNode.extraVolumes`                                      | Optionally specify extra list of additional volumes for the Data Node pod(s)                        | `[]`             |
| `dataNode.extraVolumeMounts`                                 | Optionally specify extra list of additional volumeMounts for the Data Node container(s)             | `[]`             |
| `dataNode.sidecars`                                          | Add additional sidecar containers to the Data Node pod(s)                                           | `[]`             |
| `dataNode.enableDefaultInitContainers`                       | Deploy default init containers                                                                      | `true`           |
| `dataNode.initContainers`                                    | Add additional init containers to the Data Node pod(s)                                              | `[]`             |
| `dataNode.serviceAccount.create`                             | Enable creation of ServiceAccount for Data Node pods                                                | `false`          |
| `dataNode.serviceAccount.name`                               | The name of the ServiceAccount to use                                                               | `""`             |
| `dataNode.serviceAccount.automountServiceAccountToken`       | Allows auto mount of ServiceAccountToken on the serviceAccount created                              | `false`          |
| `dataNode.serviceAccount.annotations`                        | Additional custom annotations for the ServiceAccount                                                | `{}`             |
| `dataNode.pdb.create`                                        | Enable/disable a Pod Disruption Budget creation                                                     | `false`          |
| `dataNode.pdb.minAvailable`                                  | Minimum number/percentage of pods that should remain scheduled                                      | `1`              |
| `dataNode.pdb.maxUnavailable`                                | Maximum number/percentage of pods that may be made unavailable                                      | `""`             |

### Data Node Autoscaling configuration

| Name                                               | Description                                                                                                                                                            | Value   |
| -------------------------------------------------- | ---------------------------------------------------------------------------------------------------------------------------------------------------------------------- | ------- |
| `dataNode.autoscaling.vpa.enabled`                 | Enable VPA                                                                                                                                                             | `false` |
| `dataNode.autoscaling.vpa.annotations`             | Annotations for VPA resource                                                                                                                                           | `{}`    |
| `dataNode.autoscaling.vpa.controlledResources`     | VPA List of resources that the vertical pod autoscaler can control. Defaults to cpu and memory                                                                         | `[]`    |
| `dataNode.autoscaling.vpa.maxAllowed`              | VPA Max allowed resources for the pod                                                                                                                                  | `{}`    |
| `dataNode.autoscaling.vpa.minAllowed`              | VPA Min allowed resources for the pod                                                                                                                                  | `{}`    |
| `dataNode.autoscaling.vpa.updatePolicy.updateMode` | Autoscaling update policy Specifies whether recommended updates are applied when a Pod is started and whether recommended updates are applied during the life of a Pod | `Auto`  |
| `dataNode.autoscaling.hpa.enabled`                 | Enable HPA for Milvus Data Plane                                                                                                                                       | `false` |
| `dataNode.autoscaling.hpa.annotations`             | Annotations for HPA resource                                                                                                                                           | `{}`    |
| `dataNode.autoscaling.hpa.minReplicas`             | Minimum number of Milvus Data Plane replicas                                                                                                                           | `""`    |
| `dataNode.autoscaling.hpa.maxReplicas`             | Maximum number of Milvus Data Plane replicas                                                                                                                           | `""`    |
| `dataNode.autoscaling.hpa.targetCPU`               | Target CPU utilization percentage                                                                                                                                      | `""`    |
| `dataNode.autoscaling.hpa.targetMemory`            | Target Memory utilization percentage                                                                                                                                   | `""`    |

### Data Node Traffic Exposure Parameters

| Name                                             | Description                                                      | Value       |
| ------------------------------------------------ | ---------------------------------------------------------------- | ----------- |
| `dataNode.service.type`                          | Data Node service type                                           | `ClusterIP` |
| `dataNode.service.ports.grpc`                    | Data Node GRPC service port                                      | `19530`     |
| `dataNode.service.ports.metrics`                 | Data Node Metrics service port                                   | `9091`      |
| `dataNode.service.nodePorts.grpc`                | Node port for GRPC                                               | `""`        |
| `dataNode.service.nodePorts.metrics`             | Node port for Metrics                                            | `""`        |
| `dataNode.service.sessionAffinityConfig`         | Additional settings for the sessionAffinity                      | `{}`        |
| `dataNode.service.sessionAffinity`               | Control where client requests go, to the same pod or round-robin | `None`      |
| `dataNode.service.clusterIP`                     | Data Node service Cluster IP                                     | `""`        |
| `dataNode.service.loadBalancerIP`                | Data Node service Load Balancer IP                               | `""`        |
| `dataNode.service.loadBalancerSourceRanges`      | Data Node service Load Balancer sources                          | `[]`        |
| `dataNode.service.externalTrafficPolicy`         | Data Node service external traffic policy                        | `Cluster`   |
| `dataNode.service.annotations`                   | Additional custom annotations for Data Node service              | `{}`        |
| `dataNode.service.extraPorts`                    | Extra ports to expose in the Data Node service                   | `[]`        |
| `dataNode.networkPolicy.enabled`                 | Enable creation of NetworkPolicy resources                       | `false`     |
| `dataNode.networkPolicy.allowExternal`           | The Policy model to apply                                        | `true`      |
| `dataNode.networkPolicy.extraIngress`            | Add extra ingress rules to the NetworkPolicy                     | `[]`        |
| `dataNode.networkPolicy.extraEgress`             | Add extra ingress rules to the NetworkPolicy                     | `[]`        |
| `dataNode.networkPolicy.ingressNSMatchLabels`    | Labels to match to allow traffic from other namespaces           | `{}`        |
| `dataNode.networkPolicy.ingressNSPodMatchLabels` | Pod labels to match to allow traffic from other namespaces       | `{}`        |

### Data Node Metrics Parameters

| Name                                                | Description                                                                           | Value   |
| --------------------------------------------------- | ------------------------------------------------------------------------------------- | ------- |
| `dataNode.metrics.enabled`                          | Enable metrics                                                                        | `false` |
| `dataNode.metrics.annotations`                      | Annotations for the server service in order to scrape metrics                         | `{}`    |
| `dataNode.metrics.serviceMonitor.enabled`           | Create ServiceMonitor Resource for scraping metrics using Prometheus Operator         | `false` |
| `dataNode.metrics.serviceMonitor.annotations`       | Annotations for the ServiceMonitor Resource                                           | `""`    |
| `dataNode.metrics.serviceMonitor.namespace`         | Namespace for the ServiceMonitor Resource (defaults to the Release Namespace)         | `""`    |
| `dataNode.metrics.serviceMonitor.interval`          | Interval at which metrics should be scraped.                                          | `""`    |
| `dataNode.metrics.serviceMonitor.scrapeTimeout`     | Timeout after which the scrape is ended                                               | `""`    |
| `dataNode.metrics.serviceMonitor.labels`            | Additional labels that can be used so ServiceMonitor will be discovered by Prometheus | `{}`    |
| `dataNode.metrics.serviceMonitor.selector`          | Prometheus instance selector labels                                                   | `{}`    |
| `dataNode.metrics.serviceMonitor.relabelings`       | RelabelConfigs to apply to samples before scraping                                    | `[]`    |
| `dataNode.metrics.serviceMonitor.metricRelabelings` | MetricRelabelConfigs to apply to samples before ingestion                             | `[]`    |
| `dataNode.metrics.serviceMonitor.honorLabels`       | Specify honorLabels parameter to add the scrape endpoint                              | `false` |
| `dataNode.metrics.serviceMonitor.jobLabel`          | The name of the label on the target service to use as the job name in prometheus.     | `""`    |

### Query Node Deployment Parameters

| Name                                                          | Description                                                                                         | Value            |
| ------------------------------------------------------------- | --------------------------------------------------------------------------------------------------- | ---------------- |
| `queryNode.enabled`                                           | Enable Query Node deployment                                                                        | `true`           |
| `queryNode.extraEnvVars`                                      | Array with extra environment variables to add to data node nodes                                    | `[]`             |
| `queryNode.extraEnvVarsCM`                                    | Name of existing ConfigMap containing extra env vars for data node nodes                            | `""`             |
| `queryNode.extraEnvVarsSecret`                                | Name of existing Secret containing extra env vars for data node nodes                               | `""`             |
| `queryNode.defaultConfig`                                     | Default override configuration from the common set in milvus.defaultConfig                          | `""`             |
| `queryNode.existingConfigMap`                                 | name of a ConfigMap with existing configuration for the default configuration                       | `""`             |
| `queryNode.extraConfig`                                       | Override configuration                                                                              | `{}`             |
| `queryNode.extraConfigExistingConfigMap`                      | name of a ConfigMap with existing configuration for the Dashboard                                   | `""`             |
| `queryNode.command`                                           | Override default container command (useful when using custom images)                                | `[]`             |
| `queryNode.args`                                              | Override default container args (useful when using custom images)                                   | `[]`             |
| `queryNode.replicaCount`                                      | Number of Query Node replicas to deploy                                                             | `1`              |
| `queryNode.containerPorts.grpc`                               | GRPC port for Query Node                                                                            | `19530`          |
| `queryNode.containerPorts.metrics`                            | Metrics port for Query Node                                                                         | `9091`           |
| `queryNode.livenessProbe.enabled`                             | Enable livenessProbe on Query Node nodes                                                            | `true`           |
| `queryNode.livenessProbe.initialDelaySeconds`                 | Initial delay seconds for livenessProbe                                                             | `5`              |
| `queryNode.livenessProbe.periodSeconds`                       | Period seconds for livenessProbe                                                                    | `10`             |
| `queryNode.livenessProbe.timeoutSeconds`                      | Timeout seconds for livenessProbe                                                                   | `5`              |
| `queryNode.livenessProbe.failureThreshold`                    | Failure threshold for livenessProbe                                                                 | `5`              |
| `queryNode.livenessProbe.successThreshold`                    | Success threshold for livenessProbe                                                                 | `1`              |
| `queryNode.readinessProbe.enabled`                            | Enable readinessProbe on Query Node nodes                                                           | `true`           |
| `queryNode.readinessProbe.initialDelaySeconds`                | Initial delay seconds for readinessProbe                                                            | `5`              |
| `queryNode.readinessProbe.periodSeconds`                      | Period seconds for readinessProbe                                                                   | `10`             |
| `queryNode.readinessProbe.timeoutSeconds`                     | Timeout seconds for readinessProbe                                                                  | `5`              |
| `queryNode.readinessProbe.failureThreshold`                   | Failure threshold for readinessProbe                                                                | `5`              |
| `queryNode.readinessProbe.successThreshold`                   | Success threshold for readinessProbe                                                                | `1`              |
| `queryNode.startupProbe.enabled`                              | Enable startupProbe on Query Node containers                                                        | `false`          |
| `queryNode.startupProbe.initialDelaySeconds`                  | Initial delay seconds for startupProbe                                                              | `5`              |
| `queryNode.startupProbe.periodSeconds`                        | Period seconds for startupProbe                                                                     | `10`             |
| `queryNode.startupProbe.timeoutSeconds`                       | Timeout seconds for startupProbe                                                                    | `5`              |
| `queryNode.startupProbe.failureThreshold`                     | Failure threshold for startupProbe                                                                  | `5`              |
| `queryNode.startupProbe.successThreshold`                     | Success threshold for startupProbe                                                                  | `1`              |
| `queryNode.customLivenessProbe`                               | Custom livenessProbe that overrides the default one                                                 | `{}`             |
| `queryNode.customReadinessProbe`                              | Custom readinessProbe that overrides the default one                                                | `{}`             |
| `queryNode.customStartupProbe`                                | Custom startupProbe that overrides the default one                                                  | `{}`             |
| `queryNode.resources.limits`                                  | The resources limits for the data node containers                                                   | `{}`             |
| `queryNode.resources.requests`                                | The requested resources for the data node containers                                                | `{}`             |
| `queryNode.podSecurityContext.enabled`                        | Enabled Query Node pods' Security Context                                                           | `true`           |
| `queryNode.podSecurityContext.fsGroup`                        | Set Query Node pod's Security Context fsGroup                                                       | `1001`           |
| `queryNode.containerSecurityContext.enabled`                  | Enabled containers' Security Context                                                                | `true`           |
| `queryNode.containerSecurityContext.runAsUser`                | Set containers' Security Context runAsUser                                                          | `1001`           |
| `queryNode.containerSecurityContext.runAsNonRoot`             | Set container's Security Context runAsNonRoot                                                       | `true`           |
| `queryNode.containerSecurityContext.privileged`               | Set container's Security Context privileged                                                         | `false`          |
| `queryNode.containerSecurityContext.readOnlyRootFilesystem`   | Set container's Security Context readOnlyRootFilesystem                                             | `true`           |
| `queryNode.containerSecurityContext.allowPrivilegeEscalation` | Set container's Security Context allowPrivilegeEscalation                                           | `false`          |
| `queryNode.containerSecurityContext.capabilities.drop`        | List of capabilities to be dropped                                                                  | `["ALL"]`        |
| `queryNode.containerSecurityContext.seccompProfile.type`      | Set container's Security Context seccomp profile                                                    | `RuntimeDefault` |
| `queryNode.lifecycleHooks`                                    | for the data node container(s) to automate configuration before or after startup                    | `{}`             |
| `queryNode.runtimeClassName`                                  | Name of the runtime class to be used by pod(s)                                                      | `""`             |
| `queryNode.hostAliases`                                       | data node pods host aliases                                                                         | `[]`             |
| `queryNode.podLabels`                                         | Extra labels for data node pods                                                                     | `{}`             |
| `queryNode.podAnnotations`                                    | Annotations for data node pods                                                                      | `{}`             |
| `queryNode.podAffinityPreset`                                 | Pod affinity preset. Ignored if `data node.affinity` is set. Allowed values: `soft` or `hard`       | `""`             |
| `queryNode.podAntiAffinityPreset`                             | Pod anti-affinity preset. Ignored if `data node.affinity` is set. Allowed values: `soft` or `hard`  | `soft`           |
| `queryNode.nodeAffinityPreset.type`                           | Node affinity preset type. Ignored if `data node.affinity` is set. Allowed values: `soft` or `hard` | `""`             |
| `queryNode.nodeAffinityPreset.key`                            | Node label key to match. Ignored if `data node.affinity` is set                                     | `""`             |
| `queryNode.nodeAffinityPreset.values`                         | Node label values to match. Ignored if `data node.affinity` is set                                  | `[]`             |
| `queryNode.affinity`                                          | Affinity for Query Node pods assignment                                                             | `{}`             |
| `queryNode.nodeSelector`                                      | Node labels for Query Node pods assignment                                                          | `{}`             |
| `queryNode.tolerations`                                       | Tolerations for Query Node pods assignment                                                          | `[]`             |
| `queryNode.topologySpreadConstraints`                         | Topology Spread Constraints for pod assignment spread across your cluster among failure-domains     | `[]`             |
| `queryNode.priorityClassName`                                 | Query Node pods' priorityClassName                                                                  | `""`             |
| `queryNode.schedulerName`                                     | Kubernetes pod scheduler registry                                                                   | `""`             |
| `queryNode.updateStrategy.type`                               | Query Node statefulset strategy type                                                                | `RollingUpdate`  |
| `queryNode.updateStrategy.rollingUpdate`                      | Query Node statefulset rolling update configuration parameters                                      | `{}`             |
| `queryNode.extraVolumes`                                      | Optionally specify extra list of additional volumes for the Query Node pod(s)                       | `[]`             |
| `queryNode.extraVolumeMounts`                                 | Optionally specify extra list of additional volumeMounts for the Query Node container(s)            | `[]`             |
| `queryNode.sidecars`                                          | Add additional sidecar containers to the Query Node pod(s)                                          | `[]`             |
| `queryNode.enableDefaultInitContainers`                       | Deploy default init containers                                                                      | `true`           |
| `queryNode.initContainers`                                    | Add additional init containers to the Query Node pod(s)                                             | `[]`             |
| `queryNode.serviceAccount.create`                             | Enable creation of ServiceAccount for Query Node pods                                               | `false`          |
| `queryNode.serviceAccount.name`                               | The name of the ServiceAccount to use                                                               | `""`             |
| `queryNode.serviceAccount.automountServiceAccountToken`       | Allows auto mount of ServiceAccountToken on the serviceAccount created                              | `false`          |
| `queryNode.serviceAccount.annotations`                        | Additional custom annotations for the ServiceAccount                                                | `{}`             |
| `queryNode.pdb.create`                                        | Enable/disable a Pod Disruption Budget creation                                                     | `false`          |
| `queryNode.pdb.minAvailable`                                  | Minimum number/percentage of pods that should remain scheduled                                      | `1`              |
| `queryNode.pdb.maxUnavailable`                                | Maximum number/percentage of pods that may be made unavailable                                      | `""`             |

### Query Node Autoscaling configuration

| Name                                                | Description                                                                                                                                                            | Value   |
| --------------------------------------------------- | ---------------------------------------------------------------------------------------------------------------------------------------------------------------------- | ------- |
| `queryNode.autoscaling.vpa.enabled`                 | Enable VPA                                                                                                                                                             | `false` |
| `queryNode.autoscaling.vpa.annotations`             | Annotations for VPA resource                                                                                                                                           | `{}`    |
| `queryNode.autoscaling.vpa.controlledResources`     | VPA List of resources that the vertical pod autoscaler can control. Defaults to cpu and memory                                                                         | `[]`    |
| `queryNode.autoscaling.vpa.maxAllowed`              | VPA Max allowed resources for the pod                                                                                                                                  | `{}`    |
| `queryNode.autoscaling.vpa.minAllowed`              | VPA Min allowed resources for the pod                                                                                                                                  | `{}`    |
| `queryNode.autoscaling.vpa.updatePolicy.updateMode` | Autoscaling update policy Specifies whether recommended updates are applied when a Pod is started and whether recommended updates are applied during the life of a Pod | `Auto`  |
| `queryNode.autoscaling.hpa.enabled`                 | Enable HPA for Milvus Data Plane                                                                                                                                       | `false` |
| `queryNode.autoscaling.hpa.annotations`             | Annotations for HPA resource                                                                                                                                           | `{}`    |
| `queryNode.autoscaling.hpa.minReplicas`             | Minimum number of Milvus Data Plane replicas                                                                                                                           | `""`    |
| `queryNode.autoscaling.hpa.maxReplicas`             | Maximum number of Milvus Data Plane replicas                                                                                                                           | `""`    |
| `queryNode.autoscaling.hpa.targetCPU`               | Target CPU utilization percentage                                                                                                                                      | `""`    |
| `queryNode.autoscaling.hpa.targetMemory`            | Target Memory utilization percentage                                                                                                                                   | `""`    |

### Query Node Traffic Exposure Parameters

| Name                                              | Description                                                      | Value       |
| ------------------------------------------------- | ---------------------------------------------------------------- | ----------- |
| `queryNode.service.type`                          | Query Node service type                                          | `ClusterIP` |
| `queryNode.service.ports.grpc`                    | Query Node GRPC service port                                     | `19530`     |
| `queryNode.service.ports.metrics`                 | Query Node Metrics service port                                  | `9091`      |
| `queryNode.service.nodePorts.grpc`                | Node port for GRPC                                               | `""`        |
| `queryNode.service.nodePorts.metrics`             | Node port for Metrics                                            | `""`        |
| `queryNode.service.sessionAffinityConfig`         | Additional settings for the sessionAffinity                      | `{}`        |
| `queryNode.service.sessionAffinity`               | Control where client requests go, to the same pod or round-robin | `None`      |
| `queryNode.service.clusterIP`                     | Query Node service Cluster IP                                    | `""`        |
| `queryNode.service.loadBalancerIP`                | Query Node service Load Balancer IP                              | `""`        |
| `queryNode.service.loadBalancerSourceRanges`      | Query Node service Load Balancer sources                         | `[]`        |
| `queryNode.service.externalTrafficPolicy`         | Query Node service external traffic policy                       | `Cluster`   |
| `queryNode.service.annotations`                   | Additional custom annotations for Query Node service             | `{}`        |
| `queryNode.service.extraPorts`                    | Extra ports to expose in the Query Node service                  | `[]`        |
| `queryNode.networkPolicy.enabled`                 | Enable creation of NetworkPolicy resources                       | `false`     |
| `queryNode.networkPolicy.allowExternal`           | The Policy model to apply                                        | `true`      |
| `queryNode.networkPolicy.extraIngress`            | Add extra ingress rules to the NetworkPolicy                     | `[]`        |
| `queryNode.networkPolicy.extraEgress`             | Add extra ingress rules to the NetworkPolicy                     | `[]`        |
| `queryNode.networkPolicy.ingressNSMatchLabels`    | Labels to match to allow traffic from other namespaces           | `{}`        |
| `queryNode.networkPolicy.ingressNSPodMatchLabels` | Pod labels to match to allow traffic from other namespaces       | `{}`        |

### Query Node Metrics Parameters

| Name                                                 | Description                                                                           | Value   |
| ---------------------------------------------------- | ------------------------------------------------------------------------------------- | ------- |
| `queryNode.metrics.enabled`                          | Enable metrics                                                                        | `false` |
| `queryNode.metrics.annotations`                      | Annotations for the server service in order to scrape metrics                         | `{}`    |
| `queryNode.metrics.serviceMonitor.enabled`           | Create ServiceMonitor Resource for scraping metrics using Prometheus Operator         | `false` |
| `queryNode.metrics.serviceMonitor.annotations`       | Annotations for the ServiceMonitor Resource                                           | `""`    |
| `queryNode.metrics.serviceMonitor.namespace`         | Namespace for the ServiceMonitor Resource (defaults to the Release Namespace)         | `""`    |
| `queryNode.metrics.serviceMonitor.interval`          | Interval at which metrics should be scraped.                                          | `""`    |
| `queryNode.metrics.serviceMonitor.scrapeTimeout`     | Timeout after which the scrape is ended                                               | `""`    |
| `queryNode.metrics.serviceMonitor.labels`            | Additional labels that can be used so ServiceMonitor will be discovered by Prometheus | `{}`    |
| `queryNode.metrics.serviceMonitor.selector`          | Prometheus instance selector labels                                                   | `{}`    |
| `queryNode.metrics.serviceMonitor.relabelings`       | RelabelConfigs to apply to samples before scraping                                    | `[]`    |
| `queryNode.metrics.serviceMonitor.metricRelabelings` | MetricRelabelConfigs to apply to samples before ingestion                             | `[]`    |
| `queryNode.metrics.serviceMonitor.honorLabels`       | Specify honorLabels parameter to add the scrape endpoint                              | `false` |
| `queryNode.metrics.serviceMonitor.jobLabel`          | The name of the label on the target service to use as the job name in prometheus.     | `""`    |

### Index Node Deployment Parameters

| Name                                                          | Description                                                                                         | Value            |
| ------------------------------------------------------------- | --------------------------------------------------------------------------------------------------- | ---------------- |
| `indexNode.enabled`                                           | Enable Index Node deployment                                                                        | `true`           |
| `indexNode.extraEnvVars`                                      | Array with extra environment variables to add to data node nodes                                    | `[]`             |
| `indexNode.extraEnvVarsCM`                                    | Name of existing ConfigMap containing extra env vars for data node nodes                            | `""`             |
| `indexNode.extraEnvVarsSecret`                                | Name of existing Secret containing extra env vars for data node nodes                               | `""`             |
| `indexNode.defaultConfig`                                     | Default override configuration from the common set in milvus.defaultConfig                          | `""`             |
| `indexNode.existingConfigMap`                                 | name of a ConfigMap with existing configuration for the default configuration                       | `""`             |
| `indexNode.extraConfig`                                       | Override configuration                                                                              | `{}`             |
| `indexNode.extraConfigExistingConfigMap`                      | name of a ConfigMap with existing configuration for the Dashboard                                   | `""`             |
| `indexNode.command`                                           | Override default container command (useful when using custom images)                                | `[]`             |
| `indexNode.args`                                              | Override default container args (useful when using custom images)                                   | `[]`             |
| `indexNode.replicaCount`                                      | Number of Index Node replicas to deploy                                                             | `1`              |
| `indexNode.containerPorts.grpc`                               | GRPC port for Index Node                                                                            | `19530`          |
| `indexNode.containerPorts.metrics`                            | Metrics port for Index Node                                                                         | `9091`           |
| `indexNode.livenessProbe.enabled`                             | Enable livenessProbe on Index Node nodes                                                            | `true`           |
| `indexNode.livenessProbe.initialDelaySeconds`                 | Initial delay seconds for livenessProbe                                                             | `5`              |
| `indexNode.livenessProbe.periodSeconds`                       | Period seconds for livenessProbe                                                                    | `10`             |
| `indexNode.livenessProbe.timeoutSeconds`                      | Timeout seconds for livenessProbe                                                                   | `5`              |
| `indexNode.livenessProbe.failureThreshold`                    | Failure threshold for livenessProbe                                                                 | `5`              |
| `indexNode.livenessProbe.successThreshold`                    | Success threshold for livenessProbe                                                                 | `1`              |
| `indexNode.readinessProbe.enabled`                            | Enable readinessProbe on Index Node nodes                                                           | `true`           |
| `indexNode.readinessProbe.initialDelaySeconds`                | Initial delay seconds for readinessProbe                                                            | `5`              |
| `indexNode.readinessProbe.periodSeconds`                      | Period seconds for readinessProbe                                                                   | `10`             |
| `indexNode.readinessProbe.timeoutSeconds`                     | Timeout seconds for readinessProbe                                                                  | `5`              |
| `indexNode.readinessProbe.failureThreshold`                   | Failure threshold for readinessProbe                                                                | `5`              |
| `indexNode.readinessProbe.successThreshold`                   | Success threshold for readinessProbe                                                                | `1`              |
| `indexNode.startupProbe.enabled`                              | Enable startupProbe on Index Node containers                                                        | `false`          |
| `indexNode.startupProbe.initialDelaySeconds`                  | Initial delay seconds for startupProbe                                                              | `5`              |
| `indexNode.startupProbe.periodSeconds`                        | Period seconds for startupProbe                                                                     | `10`             |
| `indexNode.startupProbe.timeoutSeconds`                       | Timeout seconds for startupProbe                                                                    | `5`              |
| `indexNode.startupProbe.failureThreshold`                     | Failure threshold for startupProbe                                                                  | `5`              |
| `indexNode.startupProbe.successThreshold`                     | Success threshold for startupProbe                                                                  | `1`              |
| `indexNode.customLivenessProbe`                               | Custom livenessProbe that overrides the default one                                                 | `{}`             |
| `indexNode.customReadinessProbe`                              | Custom readinessProbe that overrides the default one                                                | `{}`             |
| `indexNode.customStartupProbe`                                | Custom startupProbe that overrides the default one                                                  | `{}`             |
| `indexNode.resources.limits`                                  | The resources limits for the data node containers                                                   | `{}`             |
| `indexNode.resources.requests`                                | The requested resources for the data node containers                                                | `{}`             |
| `indexNode.podSecurityContext.enabled`                        | Enabled Index Node pods' Security Context                                                           | `true`           |
| `indexNode.podSecurityContext.fsGroup`                        | Set Index Node pod's Security Context fsGroup                                                       | `1001`           |
| `indexNode.containerSecurityContext.enabled`                  | Enabled containers' Security Context                                                                | `true`           |
| `indexNode.containerSecurityContext.runAsUser`                | Set containers' Security Context runAsUser                                                          | `1001`           |
| `indexNode.containerSecurityContext.runAsNonRoot`             | Set container's Security Context runAsNonRoot                                                       | `true`           |
| `indexNode.containerSecurityContext.privileged`               | Set container's Security Context privileged                                                         | `false`          |
| `indexNode.containerSecurityContext.readOnlyRootFilesystem`   | Set container's Security Context readOnlyRootFilesystem                                             | `true`           |
| `indexNode.containerSecurityContext.allowPrivilegeEscalation` | Set container's Security Context allowPrivilegeEscalation                                           | `false`          |
| `indexNode.containerSecurityContext.capabilities.drop`        | List of capabilities to be dropped                                                                  | `["ALL"]`        |
| `indexNode.containerSecurityContext.seccompProfile.type`      | Set container's Security Context seccomp profile                                                    | `RuntimeDefault` |
| `indexNode.lifecycleHooks`                                    | for the data node container(s) to automate configuration before or after startup                    | `{}`             |
| `indexNode.runtimeClassName`                                  | Name of the runtime class to be used by pod(s)                                                      | `""`             |
| `indexNode.hostAliases`                                       | data node pods host aliases                                                                         | `[]`             |
| `indexNode.podLabels`                                         | Extra labels for data node pods                                                                     | `{}`             |
| `indexNode.podAnnotations`                                    | Annotations for data node pods                                                                      | `{}`             |
| `indexNode.podAffinityPreset`                                 | Pod affinity preset. Ignored if `data node.affinity` is set. Allowed values: `soft` or `hard`       | `""`             |
| `indexNode.podAntiAffinityPreset`                             | Pod anti-affinity preset. Ignored if `data node.affinity` is set. Allowed values: `soft` or `hard`  | `soft`           |
| `indexNode.nodeAffinityPreset.type`                           | Node affinity preset type. Ignored if `data node.affinity` is set. Allowed values: `soft` or `hard` | `""`             |
| `indexNode.nodeAffinityPreset.key`                            | Node label key to match. Ignored if `data node.affinity` is set                                     | `""`             |
| `indexNode.nodeAffinityPreset.values`                         | Node label values to match. Ignored if `data node.affinity` is set                                  | `[]`             |
| `indexNode.affinity`                                          | Affinity for Index Node pods assignment                                                             | `{}`             |
| `indexNode.nodeSelector`                                      | Node labels for Index Node pods assignment                                                          | `{}`             |
| `indexNode.tolerations`                                       | Tolerations for Index Node pods assignment                                                          | `[]`             |
| `indexNode.topologySpreadConstraints`                         | Topology Spread Constraints for pod assignment spread across your cluster among failure-domains     | `[]`             |
| `indexNode.priorityClassName`                                 | Index Node pods' priorityClassName                                                                  | `""`             |
| `indexNode.schedulerName`                                     | Kubernetes pod scheduler registry                                                                   | `""`             |
| `indexNode.updateStrategy.type`                               | Index Node statefulset strategy type                                                                | `RollingUpdate`  |
| `indexNode.updateStrategy.rollingUpdate`                      | Index Node statefulset rolling update configuration parameters                                      | `{}`             |
| `indexNode.extraVolumes`                                      | Optionally specify extra list of additional volumes for the Index Node pod(s)                       | `[]`             |
| `indexNode.extraVolumeMounts`                                 | Optionally specify extra list of additional volumeMounts for the Index Node container(s)            | `[]`             |
| `indexNode.sidecars`                                          | Add additional sidecar containers to the Index Node pod(s)                                          | `[]`             |
| `indexNode.enableDefaultInitContainers`                       | Deploy default init containers                                                                      | `true`           |
| `indexNode.initContainers`                                    | Add additional init containers to the Index Node pod(s)                                             | `[]`             |
| `indexNode.serviceAccount.create`                             | Enable creation of ServiceAccount for Index Node pods                                               | `false`          |
| `indexNode.serviceAccount.name`                               | The name of the ServiceAccount to use                                                               | `""`             |
| `indexNode.serviceAccount.automountServiceAccountToken`       | Allows auto mount of ServiceAccountToken on the serviceAccount created                              | `false`          |
| `indexNode.serviceAccount.annotations`                        | Additional custom annotations for the ServiceAccount                                                | `{}`             |
| `indexNode.pdb.create`                                        | Enable/disable a Pod Disruption Budget creation                                                     | `false`          |
| `indexNode.pdb.minAvailable`                                  | Minimum number/percentage of pods that should remain scheduled                                      | `1`              |
| `indexNode.pdb.maxUnavailable`                                | Maximum number/percentage of pods that may be made unavailable                                      | `""`             |

### Index Node Autoscaling configuration

| Name                                                | Description                                                                                                                                                            | Value   |
| --------------------------------------------------- | ---------------------------------------------------------------------------------------------------------------------------------------------------------------------- | ------- |
| `indexNode.autoscaling.vpa.enabled`                 | Enable VPA                                                                                                                                                             | `false` |
| `indexNode.autoscaling.vpa.annotations`             | Annotations for VPA resource                                                                                                                                           | `{}`    |
| `indexNode.autoscaling.vpa.controlledResources`     | VPA List of resources that the vertical pod autoscaler can control. Defaults to cpu and memory                                                                         | `[]`    |
| `indexNode.autoscaling.vpa.maxAllowed`              | VPA Max allowed resources for the pod                                                                                                                                  | `{}`    |
| `indexNode.autoscaling.vpa.minAllowed`              | VPA Min allowed resources for the pod                                                                                                                                  | `{}`    |
| `indexNode.autoscaling.vpa.updatePolicy.updateMode` | Autoscaling update policy Specifies whether recommended updates are applied when a Pod is started and whether recommended updates are applied during the life of a Pod | `Auto`  |
| `indexNode.autoscaling.hpa.enabled`                 | Enable HPA for Milvus Data Plane                                                                                                                                       | `false` |
| `indexNode.autoscaling.hpa.annotations`             | Annotations for HPA resource                                                                                                                                           | `{}`    |
| `indexNode.autoscaling.hpa.minReplicas`             | Minimum number of Milvus Data Plane replicas                                                                                                                           | `""`    |
| `indexNode.autoscaling.hpa.maxReplicas`             | Maximum number of Milvus Data Plane replicas                                                                                                                           | `""`    |
| `indexNode.autoscaling.hpa.targetCPU`               | Target CPU utilization percentage                                                                                                                                      | `""`    |
| `indexNode.autoscaling.hpa.targetMemory`            | Target Memory utilization percentage                                                                                                                                   | `""`    |

### Index Node Traffic Exposure Parameters

| Name                                              | Description                                                      | Value       |
| ------------------------------------------------- | ---------------------------------------------------------------- | ----------- |
| `indexNode.service.type`                          | Index Node service type                                          | `ClusterIP` |
| `indexNode.service.ports.grpc`                    | Index Node GRPC service port                                     | `19530`     |
| `indexNode.service.ports.metrics`                 | Index Node Metrics service port                                  | `9091`      |
| `indexNode.service.nodePorts.grpc`                | Node port for GRPC                                               | `""`        |
| `indexNode.service.nodePorts.metrics`             | Node port for Metrics                                            | `""`        |
| `indexNode.service.sessionAffinityConfig`         | Additional settings for the sessionAffinity                      | `{}`        |
| `indexNode.service.sessionAffinity`               | Control where client requests go, to the same pod or round-robin | `None`      |
| `indexNode.service.clusterIP`                     | Index Node service Cluster IP                                    | `""`        |
| `indexNode.service.loadBalancerIP`                | Index Node service Load Balancer IP                              | `""`        |
| `indexNode.service.loadBalancerSourceRanges`      | Index Node service Load Balancer sources                         | `[]`        |
| `indexNode.service.externalTrafficPolicy`         | Index Node service external traffic policy                       | `Cluster`   |
| `indexNode.service.annotations`                   | Additional custom annotations for Index Node service             | `{}`        |
| `indexNode.service.extraPorts`                    | Extra ports to expose in the Index Node service                  | `[]`        |
| `indexNode.networkPolicy.enabled`                 | Enable creation of NetworkPolicy resources                       | `false`     |
| `indexNode.networkPolicy.allowExternal`           | The Policy model to apply                                        | `true`      |
| `indexNode.networkPolicy.extraIngress`            | Add extra ingress rules to the NetworkPolicy                     | `[]`        |
| `indexNode.networkPolicy.extraEgress`             | Add extra ingress rules to the NetworkPolicy                     | `[]`        |
| `indexNode.networkPolicy.ingressNSMatchLabels`    | Labels to match to allow traffic from other namespaces           | `{}`        |
| `indexNode.networkPolicy.ingressNSPodMatchLabels` | Pod labels to match to allow traffic from other namespaces       | `{}`        |

### Index Node Metrics Parameters

| Name                                                 | Description                                                                           | Value   |
| ---------------------------------------------------- | ------------------------------------------------------------------------------------- | ------- |
| `indexNode.metrics.enabled`                          | Enable metrics                                                                        | `false` |
| `indexNode.metrics.annotations`                      | Annotations for the server service in order to scrape metrics                         | `{}`    |
| `indexNode.metrics.serviceMonitor.enabled`           | Create ServiceMonitor Resource for scraping metrics using Prometheus Operator         | `false` |
| `indexNode.metrics.serviceMonitor.annotations`       | Annotations for the ServiceMonitor Resource                                           | `""`    |
| `indexNode.metrics.serviceMonitor.namespace`         | Namespace for the ServiceMonitor Resource (defaults to the Release Namespace)         | `""`    |
| `indexNode.metrics.serviceMonitor.interval`          | Interval at which metrics should be scraped.                                          | `""`    |
| `indexNode.metrics.serviceMonitor.scrapeTimeout`     | Timeout after which the scrape is ended                                               | `""`    |
| `indexNode.metrics.serviceMonitor.labels`            | Additional labels that can be used so ServiceMonitor will be discovered by Prometheus | `{}`    |
| `indexNode.metrics.serviceMonitor.selector`          | Prometheus instance selector labels                                                   | `{}`    |
| `indexNode.metrics.serviceMonitor.relabelings`       | RelabelConfigs to apply to samples before scraping                                    | `[]`    |
| `indexNode.metrics.serviceMonitor.metricRelabelings` | MetricRelabelConfigs to apply to samples before ingestion                             | `[]`    |
| `indexNode.metrics.serviceMonitor.honorLabels`       | Specify honorLabels parameter to add the scrape endpoint                              | `false` |
| `indexNode.metrics.serviceMonitor.jobLabel`          | The name of the label on the target service to use as the job name in prometheus.     | `""`    |

### Proxy Deployment Parameters

| Name                                                      | Description                                                                                     | Value            |
| --------------------------------------------------------- | ----------------------------------------------------------------------------------------------- | ---------------- |
| `proxy.enabled`                                           | Enable Proxy deployment                                                                         | `true`           |
| `proxy.extraEnvVars`                                      | Array with extra environment variables to add to proxy nodes                                    | `[]`             |
| `proxy.extraEnvVarsCM`                                    | Name of existing ConfigMap containing extra env vars for proxy nodes                            | `""`             |
| `proxy.extraEnvVarsSecret`                                | Name of existing Secret containing extra env vars for proxy nodes                               | `""`             |
| `proxy.defaultConfig`                                     | Default override configuration from the common set in milvus.defaultConfig                      | `""`             |
| `proxy.existingConfigMap`                                 | name of a ConfigMap with existing configuration for the default configuration                   | `""`             |
| `proxy.extraConfig`                                       | Override configuration                                                                          | `{}`             |
| `proxy.extraConfigExistingConfigMap`                      | name of a ConfigMap with existing configuration for the Dashboard                               | `""`             |
| `proxy.command`                                           | Override default container command (useful when using custom images)                            | `[]`             |
| `proxy.args`                                              | Override default container args (useful when using custom images)                               | `[]`             |
| `proxy.replicaCount`                                      | Number of Proxy replicas to deploy                                                              | `1`              |
| `proxy.containerPorts.grpc`                               | GRPC port for Proxy                                                                             | `19530`          |
| `proxy.containerPorts.grpcInternal`                       | GRPC internal port for Proxy                                                                    | `19529`          |
| `proxy.containerPorts.metrics`                            | Metrics port for Proxy                                                                          | `9091`           |
| `proxy.livenessProbe.enabled`                             | Enable livenessProbe on Proxy nodes                                                             | `true`           |
| `proxy.livenessProbe.initialDelaySeconds`                 | Initial delay seconds for livenessProbe                                                         | `5`              |
| `proxy.livenessProbe.periodSeconds`                       | Period seconds for livenessProbe                                                                | `10`             |
| `proxy.livenessProbe.timeoutSeconds`                      | Timeout seconds for livenessProbe                                                               | `5`              |
| `proxy.livenessProbe.failureThreshold`                    | Failure threshold for livenessProbe                                                             | `5`              |
| `proxy.livenessProbe.successThreshold`                    | Success threshold for livenessProbe                                                             | `1`              |
| `proxy.readinessProbe.enabled`                            | Enable readinessProbe on Proxy nodes                                                            | `true`           |
| `proxy.readinessProbe.initialDelaySeconds`                | Initial delay seconds for readinessProbe                                                        | `5`              |
| `proxy.readinessProbe.periodSeconds`                      | Period seconds for readinessProbe                                                               | `10`             |
| `proxy.readinessProbe.timeoutSeconds`                     | Timeout seconds for readinessProbe                                                              | `5`              |
| `proxy.readinessProbe.failureThreshold`                   | Failure threshold for readinessProbe                                                            | `5`              |
| `proxy.readinessProbe.successThreshold`                   | Success threshold for readinessProbe                                                            | `1`              |
| `proxy.startupProbe.enabled`                              | Enable startupProbe on Proxy containers                                                         | `false`          |
| `proxy.startupProbe.initialDelaySeconds`                  | Initial delay seconds for startupProbe                                                          | `5`              |
| `proxy.startupProbe.periodSeconds`                        | Period seconds for startupProbe                                                                 | `10`             |
| `proxy.startupProbe.timeoutSeconds`                       | Timeout seconds for startupProbe                                                                | `5`              |
| `proxy.startupProbe.failureThreshold`                     | Failure threshold for startupProbe                                                              | `5`              |
| `proxy.startupProbe.successThreshold`                     | Success threshold for startupProbe                                                              | `1`              |
| `proxy.customLivenessProbe`                               | Custom livenessProbe that overrides the default one                                             | `{}`             |
| `proxy.customReadinessProbe`                              | Custom readinessProbe that overrides the default one                                            | `{}`             |
| `proxy.customStartupProbe`                                | Custom startupProbe that overrides the default one                                              | `{}`             |
| `proxy.resources.limits`                                  | The resources limits for the proxy containers                                                   | `{}`             |
| `proxy.resources.requests`                                | The requested resources for the proxy containers                                                | `{}`             |
| `proxy.podSecurityContext.enabled`                        | Enabled Proxy pods' Security Context                                                            | `true`           |
| `proxy.podSecurityContext.fsGroup`                        | Set Proxy pod's Security Context fsGroup                                                        | `1001`           |
| `proxy.containerSecurityContext.enabled`                  | Enabled containers' Security Context                                                            | `true`           |
| `proxy.containerSecurityContext.runAsUser`                | Set containers' Security Context runAsUser                                                      | `1001`           |
| `proxy.containerSecurityContext.runAsNonRoot`             | Set container's Security Context runAsNonRoot                                                   | `true`           |
| `proxy.containerSecurityContext.privileged`               | Set container's Security Context privileged                                                     | `false`          |
| `proxy.containerSecurityContext.readOnlyRootFilesystem`   | Set container's Security Context readOnlyRootFilesystem                                         | `true`           |
| `proxy.containerSecurityContext.allowPrivilegeEscalation` | Set container's Security Context allowPrivilegeEscalation                                       | `false`          |
| `proxy.containerSecurityContext.capabilities.drop`        | List of capabilities to be dropped                                                              | `["ALL"]`        |
| `proxy.containerSecurityContext.seccompProfile.type`      | Set container's Security Context seccomp profile                                                | `RuntimeDefault` |
| `proxy.lifecycleHooks`                                    | for the proxy container(s) to automate configuration before or after startup                    | `{}`             |
| `proxy.runtimeClassName`                                  | Name of the runtime class to be used by pod(s)                                                  | `""`             |
| `proxy.hostAliases`                                       | proxy pods host aliases                                                                         | `[]`             |
| `proxy.podLabels`                                         | Extra labels for proxy pods                                                                     | `{}`             |
| `proxy.podAnnotations`                                    | Annotations for proxy pods                                                                      | `{}`             |
| `proxy.podAffinityPreset`                                 | Pod affinity preset. Ignored if `proxy.affinity` is set. Allowed values: `soft` or `hard`       | `""`             |
| `proxy.podAntiAffinityPreset`                             | Pod anti-affinity preset. Ignored if `proxy.affinity` is set. Allowed values: `soft` or `hard`  | `soft`           |
| `proxy.nodeAffinityPreset.type`                           | Node affinity preset type. Ignored if `proxy.affinity` is set. Allowed values: `soft` or `hard` | `""`             |
| `proxy.nodeAffinityPreset.key`                            | Node label key to match. Ignored if `proxy.affinity` is set                                     | `""`             |
| `proxy.nodeAffinityPreset.values`                         | Node label values to match. Ignored if `proxy.affinity` is set                                  | `[]`             |
| `proxy.affinity`                                          | Affinity for Proxy pods assignment                                                              | `{}`             |
| `proxy.nodeSelector`                                      | Node labels for Proxy pods assignment                                                           | `{}`             |
| `proxy.tolerations`                                       | Tolerations for Proxy pods assignment                                                           | `[]`             |
| `proxy.topologySpreadConstraints`                         | Topology Spread Constraints for pod assignment spread across your cluster among failure-domains | `[]`             |
| `proxy.priorityClassName`                                 | Proxy pods' priorityClassName                                                                   | `""`             |
| `proxy.schedulerName`                                     | Kubernetes pod scheduler registry                                                               | `""`             |
| `proxy.updateStrategy.type`                               | Proxy statefulset strategy type                                                                 | `RollingUpdate`  |
| `proxy.updateStrategy.rollingUpdate`                      | Proxy statefulset rolling update configuration parameters                                       | `{}`             |
| `proxy.extraVolumes`                                      | Optionally specify extra list of additional volumes for the Proxy pod(s)                        | `[]`             |
| `proxy.extraVolumeMounts`                                 | Optionally specify extra list of additional volumeMounts for the Proxy container(s)             | `[]`             |
| `proxy.sidecars`                                          | Add additional sidecar containers to the Proxy pod(s)                                           | `[]`             |
| `proxy.enableDefaultInitContainers`                       | Deploy default init containers                                                                  | `true`           |
| `proxy.initContainers`                                    | Add additional init containers to the Proxy pod(s)                                              | `[]`             |
| `proxy.serviceAccount.create`                             | Enable creation of ServiceAccount for Proxy pods                                                | `false`          |
| `proxy.serviceAccount.name`                               | The name of the ServiceAccount to use                                                           | `""`             |
| `proxy.serviceAccount.automountServiceAccountToken`       | Allows auto mount of ServiceAccountToken on the serviceAccount created                          | `false`          |
| `proxy.serviceAccount.annotations`                        | Additional custom annotations for the ServiceAccount                                            | `{}`             |
| `proxy.pdb.create`                                        | Enable/disable a Pod Disruption Budget creation                                                 | `false`          |
| `proxy.pdb.minAvailable`                                  | Minimum number/percentage of pods that should remain scheduled                                  | `1`              |
| `proxy.pdb.maxUnavailable`                                | Maximum number/percentage of pods that may be made unavailable                                  | `""`             |

### Proxy Autoscaling configuration

| Name                                            | Description                                                                                                                                                            | Value   |
| ----------------------------------------------- | ---------------------------------------------------------------------------------------------------------------------------------------------------------------------- | ------- |
| `proxy.autoscaling.vpa.enabled`                 | Enable VPA                                                                                                                                                             | `false` |
| `proxy.autoscaling.vpa.annotations`             | Annotations for VPA resource                                                                                                                                           | `{}`    |
| `proxy.autoscaling.vpa.controlledResources`     | VPA List of resources that the vertical pod autoscaler can control. Defaults to cpu and memory                                                                         | `[]`    |
| `proxy.autoscaling.vpa.maxAllowed`              | VPA Max allowed resources for the pod                                                                                                                                  | `{}`    |
| `proxy.autoscaling.vpa.minAllowed`              | VPA Min allowed resources for the pod                                                                                                                                  | `{}`    |
| `proxy.autoscaling.vpa.updatePolicy.updateMode` | Autoscaling update policy Specifies whether recommended updates are applied when a Pod is started and whether recommended updates are applied during the life of a Pod | `Auto`  |
| `proxy.autoscaling.hpa.enabled`                 | Enable HPA for Milvus Data Plane                                                                                                                                       | `false` |
| `proxy.autoscaling.hpa.annotations`             | Annotations for HPA resource                                                                                                                                           | `{}`    |
| `proxy.autoscaling.hpa.minReplicas`             | Minimum number of Milvus Data Plane replicas                                                                                                                           | `""`    |
| `proxy.autoscaling.hpa.maxReplicas`             | Maximum number of Milvus Data Plane replicas                                                                                                                           | `""`    |
| `proxy.autoscaling.hpa.targetCPU`               | Target CPU utilization percentage                                                                                                                                      | `""`    |
| `proxy.autoscaling.hpa.targetMemory`            | Target Memory utilization percentage                                                                                                                                   | `""`    |

### Proxy Traffic Exposure Parameters

| Name                                          | Description                                                      | Value          |
| --------------------------------------------- | ---------------------------------------------------------------- | -------------- |
| `proxy.service.type`                          | Proxy service type                                               | `LoadBalancer` |
| `proxy.service.ports.grpc`                    | Proxy GRPC service port                                          | `19530`        |
| `proxy.service.ports.metrics`                 | Proxy Metrics service port                                       | `9091`         |
| `proxy.service.nodePorts.grpc`                | Node port for GRPC                                               | `""`           |
| `proxy.service.nodePorts.metrics`             | Node port for Metrics                                            | `""`           |
| `proxy.service.sessionAffinityConfig`         | Additional settings for the sessionAffinity                      | `{}`           |
| `proxy.service.sessionAffinity`               | Control where client requests go, to the same pod or round-robin | `None`         |
| `proxy.service.clusterIP`                     | Proxy service Cluster IP                                         | `""`           |
| `proxy.service.loadBalancerIP`                | Proxy service Load Balancer IP                                   | `""`           |
| `proxy.service.loadBalancerSourceRanges`      | Proxy service Load Balancer sources                              | `[]`           |
| `proxy.service.externalTrafficPolicy`         | Proxy service external traffic policy                            | `Cluster`      |
| `proxy.service.annotations`                   | Additional custom annotations for Proxy service                  | `{}`           |
| `proxy.service.extraPorts`                    | Extra ports to expose in the Proxy service                       | `[]`           |
| `proxy.networkPolicy.enabled`                 | Enable creation of NetworkPolicy resources                       | `false`        |
| `proxy.networkPolicy.allowExternal`           | The Policy model to apply                                        | `true`         |
| `proxy.networkPolicy.extraIngress`            | Add extra ingress rules to the NetworkPolicy                     | `[]`           |
| `proxy.networkPolicy.extraEgress`             | Add extra ingress rules to the NetworkPolicy                     | `[]`           |
| `proxy.networkPolicy.ingressNSMatchLabels`    | Labels to match to allow traffic from other namespaces           | `{}`           |
| `proxy.networkPolicy.ingressNSPodMatchLabels` | Pod labels to match to allow traffic from other namespaces       | `{}`           |

### Proxy Metrics Parameters

| Name                                             | Description                                                                           | Value   |
| ------------------------------------------------ | ------------------------------------------------------------------------------------- | ------- |
| `proxy.metrics.enabled`                          | Enable metrics                                                                        | `false` |
| `proxy.metrics.annotations`                      | Annotations for the server service in order to scrape metrics                         | `{}`    |
| `proxy.metrics.serviceMonitor.enabled`           | Create ServiceMonitor Resource for scraping metrics using Prometheus Operator         | `false` |
| `proxy.metrics.serviceMonitor.annotations`       | Annotations for the ServiceMonitor Resource                                           | `""`    |
| `proxy.metrics.serviceMonitor.namespace`         | Namespace for the ServiceMonitor Resource (defaults to the Release Namespace)         | `""`    |
| `proxy.metrics.serviceMonitor.interval`          | Interval at which metrics should be scraped.                                          | `""`    |
| `proxy.metrics.serviceMonitor.scrapeTimeout`     | Timeout after which the scrape is ended                                               | `""`    |
| `proxy.metrics.serviceMonitor.labels`            | Additional labels that can be used so ServiceMonitor will be discovered by Prometheus | `{}`    |
| `proxy.metrics.serviceMonitor.selector`          | Prometheus instance selector labels                                                   | `{}`    |
| `proxy.metrics.serviceMonitor.relabelings`       | RelabelConfigs to apply to samples before scraping                                    | `[]`    |
| `proxy.metrics.serviceMonitor.metricRelabelings` | MetricRelabelConfigs to apply to samples before ingestion                             | `[]`    |
| `proxy.metrics.serviceMonitor.honorLabels`       | Specify honorLabels parameter to add the scrape endpoint                              | `false` |
| `proxy.metrics.serviceMonitor.jobLabel`          | The name of the label on the target service to use as the job name in prometheus.     | `""`    |

### Attu Deployment Parameters

| Name                                                     | Description                                                                                          | Value                  |
| -------------------------------------------------------- | ---------------------------------------------------------------------------------------------------- | ---------------------- |
| `attu.enabled`                                           | Enable Attu deployment                                                                               | `true`                 |
| `attu.image.registry`                                    | Attu image registry                                                                                  | `REGISTRY_NAME`        |
| `attu.image.repository`                                  | Attu image repository                                                                                | `REPOSITORY_NAME/attu` |
| `attu.image.digest`                                      | Attu image digest in the way sha256:aa.... Please note this parameter, if set, will override the tag | `""`                   |
| `attu.image.pullPolicy`                                  | Attu image pull policy                                                                               | `IfNotPresent`         |
| `attu.image.pullSecrets`                                 | Attu image pull secrets                                                                              | `[]`                   |
| `attu.image.debug`                                       | Enable debug mode                                                                                    | `false`                |
| `attu.extraEnvVars`                                      | Array with extra environment variables to add to attu nodes                                          | `[]`                   |
| `attu.extraEnvVarsCM`                                    | Name of existing ConfigMap containing extra env vars for attu nodes                                  | `""`                   |
| `attu.extraEnvVarsSecret`                                | Name of existing Secret containing extra env vars for attu nodes                                     | `""`                   |
| `attu.command`                                           | Override default container command (useful when using custom images)                                 | `[]`                   |
| `attu.args`                                              | Override default container args (useful when using custom images)                                    | `[]`                   |
| `attu.replicaCount`                                      | Number of Attu replicas to deploy                                                                    | `1`                    |
| `attu.containerPorts.http`                               | HTTP port for Attu                                                                                   | `3000`                 |
| `attu.livenessProbe.enabled`                             | Enable livenessProbe on Attu nodes                                                                   | `true`                 |
| `attu.livenessProbe.initialDelaySeconds`                 | Initial delay seconds for livenessProbe                                                              | `5`                    |
| `attu.livenessProbe.periodSeconds`                       | Period seconds for livenessProbe                                                                     | `10`                   |
| `attu.livenessProbe.timeoutSeconds`                      | Timeout seconds for livenessProbe                                                                    | `5`                    |
| `attu.livenessProbe.failureThreshold`                    | Failure threshold for livenessProbe                                                                  | `5`                    |
| `attu.livenessProbe.successThreshold`                    | Success threshold for livenessProbe                                                                  | `1`                    |
| `attu.readinessProbe.enabled`                            | Enable readinessProbe on Attu nodes                                                                  | `true`                 |
| `attu.readinessProbe.initialDelaySeconds`                | Initial delay seconds for readinessProbe                                                             | `5`                    |
| `attu.readinessProbe.periodSeconds`                      | Period seconds for readinessProbe                                                                    | `10`                   |
| `attu.readinessProbe.timeoutSeconds`                     | Timeout seconds for readinessProbe                                                                   | `5`                    |
| `attu.readinessProbe.failureThreshold`                   | Failure threshold for readinessProbe                                                                 | `5`                    |
| `attu.readinessProbe.successThreshold`                   | Success threshold for readinessProbe                                                                 | `1`                    |
| `attu.startupProbe.enabled`                              | Enable startupProbe on Attu containers                                                               | `false`                |
| `attu.startupProbe.initialDelaySeconds`                  | Initial delay seconds for startupProbe                                                               | `5`                    |
| `attu.startupProbe.periodSeconds`                        | Period seconds for startupProbe                                                                      | `10`                   |
| `attu.startupProbe.timeoutSeconds`                       | Timeout seconds for startupProbe                                                                     | `5`                    |
| `attu.startupProbe.failureThreshold`                     | Failure threshold for startupProbe                                                                   | `5`                    |
| `attu.startupProbe.successThreshold`                     | Success threshold for startupProbe                                                                   | `1`                    |
| `attu.customLivenessProbe`                               | Custom livenessProbe that overrides the default one                                                  | `{}`                   |
| `attu.customReadinessProbe`                              | Custom readinessProbe that overrides the default one                                                 | `{}`                   |
| `attu.customStartupProbe`                                | Custom startupProbe that overrides the default one                                                   | `{}`                   |
| `attu.resources.limits`                                  | The resources limits for the attu containers                                                         | `{}`                   |
| `attu.resources.requests`                                | The requested resources for the attu containers                                                      | `{}`                   |
| `attu.podSecurityContext.enabled`                        | Enabled Attu pods' Security Context                                                                  | `true`                 |
| `attu.podSecurityContext.fsGroup`                        | Set Attu pod's Security Context fsGroup                                                              | `1001`                 |
| `attu.containerSecurityContext.enabled`                  | Enabled containers' Security Context                                                                 | `true`                 |
| `attu.containerSecurityContext.runAsUser`                | Set containers' Security Context runAsUser                                                           | `1001`                 |
| `attu.containerSecurityContext.runAsNonRoot`             | Set container's Security Context runAsNonRoot                                                        | `true`                 |
| `attu.containerSecurityContext.privileged`               | Set container's Security Context privileged                                                          | `false`                |
| `attu.containerSecurityContext.readOnlyRootFilesystem`   | Set container's Security Context readOnlyRootFilesystem                                              | `true`                 |
| `attu.containerSecurityContext.allowPrivilegeEscalation` | Set container's Security Context allowPrivilegeEscalation                                            | `false`                |
| `attu.containerSecurityContext.capabilities.drop`        | List of capabilities to be dropped                                                                   | `["ALL"]`              |
| `attu.containerSecurityContext.seccompProfile.type`      | Set container's Security Context seccomp profile                                                     | `RuntimeDefault`       |
| `attu.lifecycleHooks`                                    | for the attu container(s) to automate configuration before or after startup                          | `{}`                   |
| `attu.runtimeClassName`                                  | Name of the runtime class to be used by pod(s)                                                       | `""`                   |
| `attu.hostAliases`                                       | attu pods host aliases                                                                               | `[]`                   |
| `attu.podLabels`                                         | Extra labels for attu pods                                                                           | `{}`                   |
| `attu.podAnnotations`                                    | Annotations for attu pods                                                                            | `{}`                   |
| `attu.podAffinityPreset`                                 | Pod affinity preset. Ignored if `attu.affinity` is set. Allowed values: `soft` or `hard`             | `""`                   |
| `attu.podAntiAffinityPreset`                             | Pod anti-affinity preset. Ignored if `attu.affinity` is set. Allowed values: `soft` or `hard`        | `soft`                 |
| `attu.nodeAffinityPreset.type`                           | Node affinity preset type. Ignored if `attu.affinity` is set. Allowed values: `soft` or `hard`       | `""`                   |
| `attu.nodeAffinityPreset.key`                            | Node label key to match. Ignored if `attu.affinity` is set                                           | `""`                   |
| `attu.nodeAffinityPreset.values`                         | Node label values to match. Ignored if `attu.affinity` is set                                        | `[]`                   |
| `attu.affinity`                                          | Affinity for Attu pods assignment                                                                    | `{}`                   |
| `attu.nodeSelector`                                      | Node labels for Attu pods assignment                                                                 | `{}`                   |
| `attu.tolerations`                                       | Tolerations for Attu pods assignment                                                                 | `[]`                   |
| `attu.topologySpreadConstraints`                         | Topology Spread Constraints for pod assignment spread across your cluster among failure-domains      | `[]`                   |
| `attu.priorityClassName`                                 | Attu pods' priorityClassName                                                                         | `""`                   |
| `attu.schedulerName`                                     | Kubernetes pod scheduler registry                                                                    | `""`                   |
| `attu.updateStrategy.type`                               | Attu statefulset strategy type                                                                       | `RollingUpdate`        |
| `attu.updateStrategy.rollingUpdate`                      | Attu statefulset rolling update configuration parameters                                             | `{}`                   |
| `attu.extraVolumes`                                      | Optionally specify extra list of additional volumes for the Attu pod(s)                              | `[]`                   |
| `attu.extraVolumeMounts`                                 | Optionally specify extra list of additional volumeMounts for the Attu container(s)                   | `[]`                   |
| `attu.sidecars`                                          | Add additional sidecar containers to the Attu pod(s)                                                 | `[]`                   |
| `attu.enableDefaultInitContainers`                       | Deploy default init containers                                                                       | `true`                 |
| `attu.initContainers`                                    | Add additional init containers to the Attu pod(s)                                                    | `[]`                   |
| `attu.serviceAccount.create`                             | Enable creation of ServiceAccount for Attu pods                                                      | `false`                |
| `attu.serviceAccount.name`                               | The name of the ServiceAccount to use                                                                | `""`                   |
| `attu.serviceAccount.automountServiceAccountToken`       | Allows auto mount of ServiceAccountToken on the serviceAccount created                               | `false`                |
| `attu.serviceAccount.annotations`                        | Additional custom annotations for the ServiceAccount                                                 | `{}`                   |
| `attu.pdb.create`                                        | Enable/disable a Pod Disruption Budget creation                                                      | `false`                |
| `attu.pdb.minAvailable`                                  | Minimum number/percentage of pods that should remain scheduled                                       | `1`                    |
| `attu.pdb.maxUnavailable`                                | Maximum number/percentage of pods that may be made unavailable                                       | `""`                   |

### Attu Autoscaling configuration

| Name                                           | Description                                                                                                                                                            | Value   |
| ---------------------------------------------- | ---------------------------------------------------------------------------------------------------------------------------------------------------------------------- | ------- |
| `attu.autoscaling.vpa.enabled`                 | Enable VPA                                                                                                                                                             | `false` |
| `attu.autoscaling.vpa.annotations`             | Annotations for VPA resource                                                                                                                                           | `{}`    |
| `attu.autoscaling.vpa.controlledResources`     | VPA List of resources that the vertical pod autoscaler can control. Defaults to cpu and memory                                                                         | `[]`    |
| `attu.autoscaling.vpa.maxAllowed`              | VPA Max allowed resources for the pod                                                                                                                                  | `{}`    |
| `attu.autoscaling.vpa.minAllowed`              | VPA Min allowed resources for the pod                                                                                                                                  | `{}`    |
| `attu.autoscaling.vpa.updatePolicy.updateMode` | Autoscaling update policy Specifies whether recommended updates are applied when a Pod is started and whether recommended updates are applied during the life of a Pod | `Auto`  |
| `attu.autoscaling.hpa.enabled`                 | Enable HPA for Milvus Data Plane                                                                                                                                       | `false` |
| `attu.autoscaling.hpa.annotations`             | Annotations for HPA resource                                                                                                                                           | `{}`    |
| `attu.autoscaling.hpa.minReplicas`             | Minimum number of Milvus Data Plane replicas                                                                                                                           | `""`    |
| `attu.autoscaling.hpa.maxReplicas`             | Maximum number of Milvus Data Plane replicas                                                                                                                           | `""`    |
| `attu.autoscaling.hpa.targetCPU`               | Target CPU utilization percentage                                                                                                                                      | `""`    |
| `attu.autoscaling.hpa.targetMemory`            | Target Memory utilization percentage                                                                                                                                   | `""`    |

### Attu Traffic Exposure Parameters

| Name                                         | Description                                                                                                                      | Value                    |
| -------------------------------------------- | -------------------------------------------------------------------------------------------------------------------------------- | ------------------------ |
| `attu.service.type`                          | Attu service type                                                                                                                | `LoadBalancer`           |
| `attu.service.ports.http`                    | Attu HTTP service port                                                                                                           | `80`                     |
| `attu.service.nodePorts.http`                | Node port for HTTP                                                                                                               | `""`                     |
| `attu.service.sessionAffinityConfig`         | Additional settings for the sessionAffinity                                                                                      | `{}`                     |
| `attu.service.sessionAffinity`               | Control where client requests go, to the same pod or round-robin                                                                 | `None`                   |
| `attu.service.clusterIP`                     | Attu service Cluster IP                                                                                                          | `""`                     |
| `attu.service.loadBalancerIP`                | Attu service Load Balancer IP                                                                                                    | `""`                     |
| `attu.service.loadBalancerSourceRanges`      | Attu service Load Balancer sources                                                                                               | `[]`                     |
| `attu.service.externalTrafficPolicy`         | Attu service external traffic policy                                                                                             | `Cluster`                |
| `attu.service.annotations`                   | Additional custom annotations for Attu service                                                                                   | `{}`                     |
| `attu.service.extraPorts`                    | Extra ports to expose in the Attu service                                                                                        | `[]`                     |
| `attu.ingress.enabled`                       | Enable ingress record generation for Milvus                                                                                      | `false`                  |
| `attu.ingress.pathType`                      | Ingress path type                                                                                                                | `ImplementationSpecific` |
| `attu.ingress.apiVersion`                    | Force Ingress API version (automatically detected if not set)                                                                    | `""`                     |
| `attu.ingress.hostname`                      | Default host for the ingress record                                                                                              | `milvus.local`           |
| `attu.ingress.ingressClassName`              | IngressClass that will be be used to implement the Ingress (Kubernetes 1.18+)                                                    | `""`                     |
| `attu.ingress.path`                          | Default path for the ingress record                                                                                              | `/`                      |
| `attu.ingress.annotations`                   | Additional annotations for the Ingress resource. To enable certificate autogeneration, place here your cert-manager annotations. | `{}`                     |
| `attu.ingress.tls`                           | Enable TLS configuration for the host defined at `attu.ingress.hostname` parameter                                               | `false`                  |
| `attu.ingress.selfSigned`                    | Create a TLS secret for this ingress record using self-signed certificates generated by Helm                                     | `false`                  |
| `attu.ingress.extraHosts`                    | An array with additional hostname(s) to be covered with the ingress record                                                       | `[]`                     |
| `attu.ingress.extraPaths`                    | An array with additional arbitrary paths that may need to be added to the ingress under the main host                            | `[]`                     |
| `attu.ingress.extraTls`                      | TLS configuration for additional hostname(s) to be covered with this ingress record                                              | `[]`                     |
| `attu.ingress.secrets`                       | Custom TLS certificates as secrets                                                                                               | `[]`                     |
| `attu.ingress.extraRules`                    | Additional rules to be covered with this ingress record                                                                          | `[]`                     |
| `attu.networkPolicy.enabled`                 | Enable creation of NetworkPolicy resources                                                                                       | `false`                  |
| `attu.networkPolicy.allowExternal`           | The Policy model to apply                                                                                                        | `true`                   |
| `attu.networkPolicy.extraIngress`            | Add extra ingress rules to the NetworkPolicy                                                                                     | `[]`                     |
| `attu.networkPolicy.extraEgress`             | Add extra ingress rules to the NetworkPolicy                                                                                     | `[]`                     |
| `attu.networkPolicy.ingressNSMatchLabels`    | Labels to match to allow traffic from other namespaces                                                                           | `{}`                     |
| `attu.networkPolicy.ingressNSPodMatchLabels` | Pod labels to match to allow traffic from other namespaces                                                                       | `{}`                     |

### Init Container Parameters

| Name                                                              | Description                                                                                                                   | Value                      |
| ----------------------------------------------------------------- | ----------------------------------------------------------------------------------------------------------------------------- | -------------------------- |
| `waitContainer.image.registry`                                    | Init container wait-container image registry                                                                                  | `REGISTRY_NAME`            |
| `waitContainer.image.repository`                                  | Init container wait-container image name                                                                                      | `REPOSITORY_NAME/os-shell` |
| `waitContainer.image.digest`                                      | Init container wait-container image digest in the way sha256:aa.... Please note this parameter, if set, will override the tag | `""`                       |
| `waitContainer.image.pullPolicy`                                  | Init container wait-container image pull policy                                                                               | `IfNotPresent`             |
| `waitContainer.image.pullSecrets`                                 | Specify docker-registry secret names as an array                                                                              | `[]`                       |
| `waitContainer.containerSecurityContext.enabled`                  | Enabled containers' Security Context                                                                                          | `true`                     |
| `waitContainer.containerSecurityContext.runAsUser`                | Set containers' Security Context runAsUser                                                                                    | `1001`                     |
| `waitContainer.containerSecurityContext.runAsNonRoot`             | Set container's Security Context runAsNonRoot                                                                                 | `true`                     |
| `waitContainer.containerSecurityContext.privileged`               | Set container's Security Context privileged                                                                                   | `false`                    |
| `waitContainer.containerSecurityContext.readOnlyRootFilesystem`   | Set container's Security Context readOnlyRootFilesystem                                                                       | `true`                     |
| `waitContainer.containerSecurityContext.allowPrivilegeEscalation` | Set container's Security Context allowPrivilegeEscalation                                                                     | `false`                    |
| `waitContainer.containerSecurityContext.capabilities.drop`        | List of capabilities to be dropped                                                                                            | `["ALL"]`                  |
| `waitContainer.containerSecurityContext.seccompProfile.type`      | Set container's Security Context seccomp profile                                                                              | `RuntimeDefault`           |

### External etcd settings

| Name                                     | Description                                                                                          | Value                |
| ---------------------------------------- | ---------------------------------------------------------------------------------------------------- | -------------------- |
| `externalEtcd.servers`                   | List of hostnames of the external etcd                                                               | `[]`                 |
| `externalEtcd.port`                      | Port of the external etcd instance                                                                   | `2379`               |
| `externalEtcd.user`                      | User of the external etcd instance                                                                   | `root`               |
| `externalEtcd.password`                  | Password of the external etcd instance                                                               | `""`                 |
| `externalEtcd.existingSecret`            | Name of a secret containing the external etcd password                                               | `""`                 |
| `externalEtcd.existingSecretPasswordKey` | Key inside the secret containing the external etcd password                                          | `etcd-root-password` |
| `externalEtcd.tls.enabled`               | Enable TLS for etcd client connections.                                                              | `false`              |
| `externalEtcd.tls.existingSecret`        | Name of the existing secret containing the TLS certificates for external etcd client communications. | `""`                 |
| `externalEtcd.tls.cert`                  | The secret key from the existingSecret if 'cert' key different from the default (tls.crt)            | `tls.crt`            |
| `externalEtcd.tls.key`                   | The secret key from the existingSecret if 'key' key different from the default (tls.key)             | `tls.key`            |
| `externalEtcd.tls.caCert`                | The secret key from the existingSecret if 'caCert' key different from the default (ca.crt)           | `ca.crt`             |
| `externalEtcd.tls.keyPassword`           | Password to access the password-protected PEM key if necessary.                                      | `""`                 |

### External S3 parameters

| Name                                      | Description                                                        | Value           |
| ----------------------------------------- | ------------------------------------------------------------------ | --------------- |
| `externalS3.host`                         | External S3 host                                                   | `""`            |
| `externalS3.port`                         | External S3 port number                                            | `443`           |
| `externalS3.accessKeyID`                  | External S3 access key ID                                          | `""`            |
| `externalS3.accessKeySecret`              | External S3 access key secret                                      | `""`            |
| `externalS3.existingSecret`               | Name of an existing secret resource containing the S3 credentials  | `""`            |
| `externalS3.existingSecretAccessKeyIDKey` | Name of an existing secret key containing the S3 access key ID     | `root-user`     |
| `externalS3.existingSecretKeySecretKey`   | Name of an existing secret key containing the S3 access key secret | `root-password` |
| `externalS3.protocol`                     | External S3 protocol                                               | `https`         |
| `externalS3.bucket`                       | External S3 bucket                                                 | `milvus`        |
| `externalS3.rootPath`                     | External S3 root path                                              | `file`          |
| `externalS3.iamEndpoint`                  | External S3 IAM endpoint                                           | `""`            |
| `externalS3.cloudProvider`                | External S3 cloud provider                                         | `""`            |

### External Kafka parameters

| Name                                           | Description                                                                                                        | Value                 |
| ---------------------------------------------- | ------------------------------------------------------------------------------------------------------------------ | --------------------- |
| `externalKafka.servers`                        | External Kafka brokers                                                                                             | `["localhost"]`       |
| `externalKafka.port`                           | External Kafka port                                                                                                | `9092`                |
| `externalKafka.listener.protocol`              | Kafka listener protocol. Allowed protocols: PLAINTEXT, SASL_PLAINTEXT, SASL_SSL and SSL                            | `PLAINTEXT`           |
| `externalKafka.sasl.user`                      | User for SASL authentication                                                                                       | `user`                |
| `externalKafka.sasl.password`                  | Password for SASL authentication                                                                                   | `""`                  |
| `externalKafka.sasl.existingSecret`            | Name of the existing secret containing a password for SASL authentication (under the key named "client-passwords") | `""`                  |
| `externalKafka.sasl.existingSecretPasswordKey` | Name of the secret key containing the Kafka client user password                                                   | `kafka-root-password` |
| `externalKafka.sasl.enabledMechanisms`         | Kafka enabled SASL mechanisms                                                                                      | `PLAIN`               |

### etcd sub-chart parameters

| Name                               | Description                                 | Value   |
| ---------------------------------- | ------------------------------------------- | ------- |
| `etcd.enabled`                     | Deploy etcd sub-chart                       | `true`  |
| `etcd.replicaCount`                | Number of etcd replicas                     | `3`     |
| `etcd.containerPorts.client`       | Container port for etcd                     | `2379`  |
| `etcd.auth.rbac.create`            | Switch to enable RBAC authentication        | `false` |
| `etcd.auth.client.secureTransport` | use TLS for client-to-server communications | `false` |

### MinIO&reg; chart parameters

| Name                               | Description                                                                                                                       | Value                                               |
| ---------------------------------- | --------------------------------------------------------------------------------------------------------------------------------- | --------------------------------------------------- |
| `minio`                            | For full list of MinIO&reg; values configurations please refere [here](https://github.com/bitnami/charts/tree/main/bitnami/minio) |                                                     |
| `minio.enabled`                    | Enable/disable MinIO&reg; chart installation                                                                                      | `true`                                              |
| `minio.auth.rootUser`              | MinIO&reg; root username                                                                                                          | `admin`                                             |
| `minio.auth.rootPassword`          | Password for MinIO&reg; root user                                                                                                 | `""`                                                |
| `minio.auth.existingSecret`        | Name of an existing secret containing the MinIO&reg; credentials                                                                  | `""`                                                |
| `minio.defaultBuckets`             | Comma, semi-colon or space separated list of MinIO&reg; buckets to create                                                         | `milvus`                                            |
| `minio.provisioning.enabled`       | Enable/disable MinIO&reg; provisioning job                                                                                        | `true`                                              |
| `minio.provisioning.extraCommands` | Extra commands to run on MinIO&reg; provisioning job                                                                              | `["mc anonymous set download provisioning/milvus"]` |
| `minio.tls.enabled`                | Enable/disable MinIO&reg; TLS support                                                                                             | `false`                                             |
| `minio.service.type`               | MinIO&reg; service type                                                                                                           | `ClusterIP`                                         |
| `minio.service.loadBalancerIP`     | MinIO&reg; service LoadBalancer IP                                                                                                | `""`                                                |
| `minio.service.ports.api`          | MinIO&reg; service port                                                                                                           | `80`                                                |

### kafka sub-chart paramaters

| Name                              | Description                                                                                   | Value                                |
| --------------------------------- | --------------------------------------------------------------------------------------------- | ------------------------------------ |
| `kafka.enabled`                   | Enable/disable Kafka chart installation                                                       | `true`                               |
| `kafka.controller.replicaCount`   | Number of Kafka controller eligible (controller+broker) nodes                                 | `1`                                  |
| `kafka.service.ports.client`      | Kafka svc port for client connections                                                         | `9092`                               |
| `kafka.extraConfig`               | Additional configuration to be appended at the end of the generated Kafka configuration file. | `offsets.topic.replication.factor=1` |
| `kafka.listeners.client.protocol` | Kafka authentication protocol for the client listener                                         | `SASL_PLAINTEXT`                     |
| `kafka.sasl.enabledMechanisms`    | Kafka enabled SASL mechanisms                                                                 | `PLAIN`                              |
| `kafka.sasl.client.users`         | Kafka client users                                                                            | `["user"]`                           |

See <https://github.com/bitnami-labs/readme-generator-for-helm> to create the table.

The above parameters map to the env variables defined in [bitnami/milvus](https://github.com/bitnami/containers/tree/main/bitnami/milvus). For more information please refer to the [bitnami/milvus](https://github.com/bitnami/containers/tree/main/bitnami/milvus) image documentation.

Specify each parameter using the `--set key=value[,key=value]` argument to `helm install`. For example,

```console
helm install my-release \
  --set loki.traces.jaeger.grpc=true \
  oci://REGISTRY_NAME/REPOSITORY_NAME/milvus
```

> Note: You need to substitute the placeholders `REGISTRY_NAME` and `REPOSITORY_NAME` with a reference to your Helm chart registry and repository. For example, in the case of Bitnami, you need to use `REGISTRY_NAME=registry-1.docker.io` and `REPOSITORY_NAME=bitnamicharts`.

The above command enables the Jaeger GRPC traces.

Alternatively, a YAML file that specifies the values for the above parameters can be provided while installing the chart. For example,

```console
helm install my-release -f values.yaml oci://REGISTRY_NAME/REPOSITORY_NAME/milvus
```

> Note: You need to substitute the placeholders `REGISTRY_NAME` and `REPOSITORY_NAME` with a reference to your Helm chart registry and repository. For example, in the case of Bitnami, you need to use `REGISTRY_NAME=registry-1.docker.io` and `REPOSITORY_NAME=bitnamicharts`.
> **Tip**: You can use the default [values.yaml](values.yaml)

## Configuration and installation details

### [Rolling VS Immutable tags](https://docs.bitnami.com/containers/how-to/understand-rolling-tags-containers/)

It is strongly recommended to use immutable tags in a production environment. This ensures your deployment does not change automatically if the same tag is updated with a different image.

Bitnami will release a new chart updating its containers if a new version of the main container, significant changes, or critical vulnerabilities exist.

### Milvus configuration

The Milvus configuration file `milvus.yaml` is shared across the different components: `rootCoord`, `dataCoord`, `indexCoord`, `dataNode` and `indexNode`. This is set in the `milvus.defaultConfig` value. This configuration can be extended with extra settings using the `milvus.extraConfig` value. For specific component configuration edit the `extraConfig` section inside each of the previously mentioned components. Check the official [Milvis documentation](https://milvus.io/docs) for the list of possible configurations.

### Additional environment variables

In case you want to add extra environment variables (useful for advanced operations like custom init scripts), you can use the `extraEnvVars` property inside each of the subsections: `rootCoord`, `dataCoord`, `indexCoord`, `dataNode`, `indexNode`, `attu` and `queryNode`.

```yaml
dataCoord:
  extraEnvVars:
    - name: LOG_LEVEL
      value: error

rootCoord:
  extraEnvVars:
    - name: LOG_LEVEL
      value: error

indexCoord:
  extraEnvVars:
    - name: LOG_LEVEL
      value: error

dataNode:
  extraEnvVars:
    - name: LOG_LEVEL
      value: error

indexNode:
  extraEnvVars:
    - name: LOG_LEVEL
      value: error

queryNode:
  extraEnvVars:
    - name: LOG_LEVEL
      value: error
```

Alternatively, you can use a ConfigMap or a Secret with the environment variables. To do so, use the `extraEnvVarsCM` or the `extraEnvVarsSecret` values.

### Sidecars

If additional containers are needed in the same pod as milvus (such as additional metrics or logging exporters), they can be defined using the `sidecars` parameter inside each of the subsections: `rootCoord`, `dataCoord`, `indexCoord`, `dataNode`, `indexNode`, `attu` and `queryNode` . If these sidecars export extra ports, extra port definitions can be added using the `service.extraPorts` parameter. [Learn more about configuring and using sidecar containers](https://docs.bitnami.com/kubernetes/infrastructure/milvus/configuration/configure-sidecar-init-containers/).

### Pod affinity

This chart allows you to set your custom affinity using the `affinity` parameter. Find more information about Pod affinity in the [kubernetes documentation](https://kubernetes.io/docs/concepts/configuration/assign-pod-node/#affinity-and-anti-affinity).

As an alternative, use one of the preset configurations for pod affinity, pod anti-affinity, and node affinity available at the [bitnami/common](https://github.com/bitnami/charts/tree/main/bitnami/common#affinities) chart. To do so, set the `podAffinityPreset`, `podAntiAffinityPreset`, or `nodeAffinityPreset` parameters inside each of the subsections: `rootCoord`, `dataCoord`, `indexCoord`, `dataNode`, `indexNode`, `attu` and `queryNode`.

### External kafka support

You may want to have Milvus connect to an external kafka rather than installing one inside your cluster. Typical reasons for this are to use a managed database service, or to share a common database server for all your applications. To achieve this, the chart allows you to specify credentials for an external database with the [`externalKafka` parameter](#parameters). You should also disable the etcd installation with the `etcd.enabled` option. Here is an example:

```yaml
kafka:
  enabled: false
externalKafka:
  hosts:
    - externalhost
```

### External etcd support

You may want to have Milvus connect to an external etcd rather than installing one inside your cluster. Typical reasons for this are to use a managed database service, or to share a common database server for all your applications. To achieve this, the chart allows you to specify credentials for an external database with the [`externalEtcd` parameter](#parameters). You should also disable the etcd installation with the `etcd.enabled` option. Here is an example:

```yaml
etcd:
  enabled: false
externalEtcd:
  hosts:
    - externalhost
```

### External S3 support

You may want to have mastodon connect to an external storage streaming rather than installing MiniIO(TM) inside your cluster. To achieve this, the chart allows you to specify credentials for an external storage streaming with the [`externalS3` parameter](#parameters). You should also disable the MinIO(TM) installation with the `minio.enabled` option. Here is an example:

```console
minio.enabled=false
externalS3.host=myexternalhost
exterernalS3.accessKeyID=accesskey
externalS3.accessKeySecret=secret
```

### Ingress

This chart provides support for Ingress resources. If you have an ingress controller installed on your cluster, such as [nginx-ingress-controller](https://github.com/bitnami/charts/tree/main/bitnami/nginx-ingress-controller) or [contour](https://github.com/bitnami/charts/tree/main/bitnami/contour) you can utilize the ingress controller to serve your application.

To enable Ingress integration, set `attu.ingress.enabled` to `true`. The `attu.ingress.hostname` property can be used to set the host name. The `attu.ingress.tls` parameter can be used to add the TLS configuration for this host. It is also possible to have more than one host, with a separate TLS configuration for each host. [Learn more about configuring and using Ingress](https://docs.bitnami.com/kubernetes/apps/mastodon/configuration/configure-ingress/).

### TLS secrets

The chart also facilitates the creation of TLS secrets for use with the Ingress controller, with different options for certificate management. [Learn more about TLS secrets](https://docs.bitnami.com/kubernetes/apps/mastodon/administration/enable-tls-ingress/).

## Upgrading

### To 4.0.0

This major updates the Kafka subchart to its newest major, 26.0.0. For more information on this subchart's major, please refer to [Kafka upgrade notes](https://github.com/bitnami/charts/tree/main/bitnami/kafka#to-2600).

### To 3.0.0

This major updates the Kafka subchart to its newest major, 25.0.0. For more information on this subchart's major, please refer to [Kafka upgrade notes](https://github.com/bitnami/charts/tree/main/bitnami/kafka#to-2500).

### To 2.0.0

This major updates the Kafka subchart to its newest major, 24.0.0. This new version refactors the Kafka chart architecture and requires manual actions during the upgrade. For more information on this subchart's major, please refer to [Kafka upgrade notes](https://github.com/bitnami/charts/tree/main/bitnami/kafka#to-2400).

Additionally, the following values have been modified:

- `externalKafka.securityProtocol` has been replaced with `externalKafka.listener.protocol`, which now allows Kafka security protocols 'PLAINTEXT','SASL_PLAINTEXT', 'SSL', 'SASL_SSL'.
- `externalKafka.user` has been replaced with `externalAccess.sasl.user`.
- `externalKafka.password` has been replaced with `externalAccess.sasl.password`.
- `externalKafka.existingSecret` has been replaced with `externalAccess.sasl.existingSecret`.
- `externalKafka.existingSecretPasswordKey` has been replaced with `externalAccess.sasl.existingSecretPasswordKey`.
- `externalKafka.saslMechanisms` has been replaced with `externalAccess.sasl.enabledMechanisms`.

### To 1.0.0

This major updates the Kafka subchart to its newest major, 23.0.0. For more information on this subchart's major, please refer to [Kafka upgrade notes](https://github.com/bitnami/charts/tree/main/bitnami/kafka#to-2300).

## Troubleshooting

Find more information about how to deal with common errors related to Bitnami's Helm charts in [this troubleshooting guide](https://docs.bitnami.com/general/how-to/troubleshoot-helm-chart-issues).

## License

Copyright &copy; 2023 VMware, Inc.

Licensed under the Apache License, Version 2.0 (the "License");
you may not use this file except in compliance with the License.
You may obtain a copy of the License at

<http://www.apache.org/licenses/LICENSE-2.0>

Unless required by applicable law or agreed to in writing, software
distributed under the License is distributed on an "AS IS" BASIS,
WITHOUT WARRANTIES OR CONDITIONS OF ANY KIND, either express or implied.
See the License for the specific language governing permissions and
limitations under the License.