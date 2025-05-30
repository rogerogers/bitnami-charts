<!--- app-name: MongoDB&reg; Sharded -->

# MongoDB(R) Sharded packaged by Bitnami

MongoDB(R) is an open source NoSQL database that uses JSON for data storage. MongoDB(TM) Sharded improves scalability and reliability for large datasets by distributing data across multiple machines.

[Overview of MongoDB&reg; Sharded](http://www.mongodb.org)

Disclaimer: The respective trademarks mentioned in the offering are owned by the respective companies. We do not provide a commercial license for any of these products. This listing has an open-source license. MongoDB(R) is run and maintained by MongoDB, which is a completely separate project from Bitnami.

## TL;DR

```console
helm install my-release oci://REGISTRY_NAME/REPOSITORY_NAME/mongodb-sharded
```

> Note: You need to substitute the placeholders `REGISTRY_NAME` and `REPOSITORY_NAME` with a reference to your Helm chart registry and repository. For example, in the case of Bitnami, you need to use `REGISTRY_NAME=registry-1.docker.io` and `REPOSITORY_NAME=bitnamicharts`.

## Introduction

This chart bootstraps a [MongoDB(&reg;) Sharded](https://github.com/bitnami/containers/tree/main/bitnami/mongodb-sharded) deployment on a [Kubernetes](https://kubernetes.io) cluster using the [Helm](https://helm.sh) package manager.

Classified as a NoSQL database, MongoDB&reg; eschews the traditional table-based relational database structure in favor of JSON-like documents with dynamic schemas, making the integration of data in certain types of applications easier and faster.

This chart uses the [sharding method](https://docs.mongodb.com/manual/sharding/) for distributing data across multiple machines. This is meant for deployments with very large data sets and high throughput operations.

Bitnami charts can be used with [Kubeapps](https://kubeapps.dev/) for deployment and management of Helm Charts in clusters.

Looking to use MongoDBreg; Sharded in production? Try [VMware Tanzu Application Catalog](https://bitnami.com/enterprise), the enterprise edition of Bitnami Application Catalog.

## Prerequisites

- Kubernetes 1.23+
- Helm 3.8.0+
- PV provisioner support in the underlying infrastructure
- ReadWriteMany volumes for deployment scaling

## Installing the Chart

To install the chart with the release name `my-release`:

```console
helm install my-release oci://REGISTRY_NAME/REPOSITORY_NAME/mongodb-sharded
```

> Note: You need to substitute the placeholders `REGISTRY_NAME` and `REPOSITORY_NAME` with a reference to your Helm chart registry and repository. For example, in the case of Bitnami, you need to use `REGISTRY_NAME=registry-1.docker.io` and `REPOSITORY_NAME=bitnamicharts`.

The command deploys MongoDB&reg; on the Kubernetes cluster in the default configuration. The [Parameters](#parameters) section lists the parameters that can be configured during installation.

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
| `global.storageClass`     | Global storage class for dynamic provisioning   | `""`  |

### Common parameters

| Name                     | Description                                                                             | Value           |
| ------------------------ | --------------------------------------------------------------------------------------- | --------------- |
| `kubeVersion`            | Override Kubernetes version                                                             | `""`            |
| `nameOverride`           | String to partially override common.names.name                                          | `""`            |
| `fullnameOverride`       | String to fully override common.names.fullname                                          | `""`            |
| `namespaceOverride`      | String to fully override common.names.namespace                                         | `""`            |
| `commonLabels`           | Labels to add to all deployed objects                                                   | `{}`            |
| `commonAnnotations`      | Annotations to add to all deployed objects                                              | `{}`            |
| `clusterDomain`          | Kubernetes cluster domain name                                                          | `cluster.local` |
| `extraDeploy`            | Array of extra objects to deploy with the release                                       | `[]`            |
| `diagnosticMode.enabled` | Enable diagnostic mode (all probes will be disabled and the command will be overridden) | `false`         |
| `diagnosticMode.command` | Command to override all containers in the deployment                                    | `["sleep"]`     |
| `diagnosticMode.args`    | Args to override all containers in the deployment                                       | `["infinity"]`  |

### MongoDB(&reg;) Sharded parameters

| Name                                                 | Description                                                                                                                                               | Value                             |
| ---------------------------------------------------- | --------------------------------------------------------------------------------------------------------------------------------------------------------- | --------------------------------- |
| `image.registry`                                     | MongoDB(&reg;) Sharded image registry                                                                                                                     | `REGISTRY_NAME`                   |
| `image.repository`                                   | MongoDB(&reg;) Sharded Image name                                                                                                                         | `REPOSITORY_NAME/mongodb-sharded` |
| `image.digest`                                       | MongoDB(&reg;) Sharded image digest in the way sha256:aa.... Please note this parameter, if set, will override the tag                                    | `""`                              |
| `image.pullPolicy`                                   | MongoDB(&reg;) Sharded image pull policy                                                                                                                  | `IfNotPresent`                    |
| `image.pullSecrets`                                  | Specify docker-registry secret names as an array                                                                                                          | `[]`                              |
| `image.debug`                                        | Specify if debug logs should be enabled                                                                                                                   | `false`                           |
| `auth.enabled`                                       | Enable authentication                                                                                                                                     | `true`                            |
| `auth.rootUser`                                      | MongoDB(&reg;) root user                                                                                                                                  | `root`                            |
| `auth.rootPassword`                                  | MongoDB(&reg;) root password                                                                                                                              | `""`                              |
| `auth.replicaSetKey`                                 | Key used for authentication in the replicaset (only when `architecture=replicaset`)                                                                       | `""`                              |
| `auth.existingSecret`                                | Existing secret with MongoDB(&reg;) credentials (keys: `mongodb-password`, `mongodb-root-password`, `mongodb-replica-set-key`)                            | `""`                              |
| `auth.usePasswordFile`                               | Mount credentials as files instead of using environment variables                                                                                         | `false`                           |
| `shards`                                             | Number of shards to be created                                                                                                                            | `2`                               |
| `common.mongodbEnableNumactl`                        | Enable launch MongoDB instance prefixed with "numactl --interleave=all"                                                                                   | `false`                           |
| `common.useHostnames`                                | Enable DNS hostnames in the replica set config                                                                                                            | `true`                            |
| `common.mongodbEnableIPv6`                           | Switch to enable/disable IPv6 on MongoDB&reg;                                                                                                             | `false`                           |
| `common.mongodbDirectoryPerDB`                       | Switch to enable/disable DirectoryPerDB on MongoDB&reg;                                                                                                   | `false`                           |
| `common.mongodbSystemLogVerbosity`                   | MongoDB&reg; system log verbosity level                                                                                                                   | `0`                               |
| `common.mongodbDisableSystemLog`                     | Whether to disable MongoDB&reg; system log or not                                                                                                         | `false`                           |
| `common.mongodbMaxWaitTimeout`                       | Maximum time (in seconds) for MongoDB&reg; nodes to wait for another MongoDB&reg; node to be ready                                                        | `120`                             |
| `common.initScriptsCM`                               | Configmap with init scripts to execute                                                                                                                    | `""`                              |
| `common.initScriptsSecret`                           | Secret with init scripts to execute (for sensitive data)                                                                                                  | `""`                              |
| `common.extraEnvVars`                                | An array to add extra env vars                                                                                                                            | `[]`                              |
| `common.extraEnvVarsCM`                              | Name of a ConfigMap containing extra env vars                                                                                                             | `""`                              |
| `common.extraEnvVarsSecret`                          | Name of a Secret containing extra env vars                                                                                                                | `""`                              |
| `common.sidecars`                                    | Add sidecars to the pod                                                                                                                                   | `[]`                              |
| `common.initContainers`                              | Add init containers to the pod                                                                                                                            | `[]`                              |
| `common.podAnnotations`                              | Additional pod annotations                                                                                                                                | `{}`                              |
| `common.podLabels`                                   | Additional pod labels                                                                                                                                     | `{}`                              |
| `common.extraVolumes`                                | Array to add extra volumes                                                                                                                                | `[]`                              |
| `common.extraVolumeMounts`                           | Array to add extra mounts (normally used with extraVolumes)                                                                                               | `[]`                              |
| `common.containerPorts.mongodb`                      | MongoDB container port                                                                                                                                    | `27017`                           |
| `common.serviceAccount.create`                       | Whether to create a Service Account for all pods automatically                                                                                            | `false`                           |
| `common.serviceAccount.name`                         | Name of a Service Account to be used by all Pods                                                                                                          | `""`                              |
| `common.serviceAccount.annotations`                  | Additional Service Account annotations (evaluated as a template)                                                                                          | `{}`                              |
| `common.serviceAccount.automountServiceAccountToken` | Automount service account token for the server service account                                                                                            | `true`                            |
| `volumePermissions.enabled`                          | Enable init container that changes volume permissions in the data directory (for cases where the default k8s `runAsUser` and `fsUser` values do not work) | `false`                           |
| `volumePermissions.image.registry`                   | Init container volume-permissions image registry                                                                                                          | `REGISTRY_NAME`                   |
| `volumePermissions.image.repository`                 | Init container volume-permissions image name                                                                                                              | `REPOSITORY_NAME/os-shell`        |
| `volumePermissions.image.digest`                     | Init container volume-permissions image digest in the way sha256:aa.... Please note this parameter, if set, will override the tag                         | `""`                              |
| `volumePermissions.image.pullPolicy`                 | Init container volume-permissions image pull policy                                                                                                       | `IfNotPresent`                    |
| `volumePermissions.image.pullSecrets`                | Init container volume-permissions image pull secrets                                                                                                      | `[]`                              |
| `volumePermissions.resources`                        | Init container resource requests/limit                                                                                                                    | `{}`                              |
| `service.name`                                       | Specify an explicit service name                                                                                                                          | `""`                              |
| `service.annotations`                                | Additional service annotations (evaluate as a template)                                                                                                   | `{}`                              |
| `service.type`                                       | Service type                                                                                                                                              | `ClusterIP`                       |
| `service.externalTrafficPolicy`                      | External traffic policy                                                                                                                                   | `Cluster`                         |
| `service.ports.mongodb`                              | MongoDB&reg; service port                                                                                                                                 | `27017`                           |
| `service.clusterIP`                                  | Static clusterIP or None for headless services                                                                                                            | `""`                              |
| `service.nodePorts.mongodb`                          | Specify the nodePort value for the LoadBalancer and NodePort service types.                                                                               | `""`                              |
| `service.externalIPs`                                | External IP list to use with ClusterIP service type                                                                                                       | `[]`                              |
| `service.loadBalancerIP`                             | Static IP Address to use for LoadBalancer service type                                                                                                    | `""`                              |
| `service.loadBalancerSourceRanges`                   | List of IP ranges allowed access to load balancer (if supported)                                                                                          | `[]`                              |
| `service.extraPorts`                                 | Extra ports to expose (normally used with the `sidecar` value)                                                                                            | `[]`                              |
| `service.sessionAffinity`                            | Session Affinity for Kubernetes service, can be "None" or "ClientIP"                                                                                      | `None`                            |
| `service.sessionAffinityConfig`                      | Additional settings for the sessionAffinity                                                                                                               | `{}`                              |
| `service.headless.annotations`                       | Annotations for the headless service.                                                                                                                     | `{}`                              |

### Config Server parameters

| Name                                                          | Description                                                                                                                           | Value                                                  |
| ------------------------------------------------------------- | ------------------------------------------------------------------------------------------------------------------------------------- | ------------------------------------------------------ |
| `configsvr.replicaCount`                                      | Number of nodes in the replica set (the first node will be primary)                                                                   | `1`                                                    |
| `configsvr.resources`                                         | Configure pod resources                                                                                                               | `{}`                                                   |
| `configsvr.hostAliases`                                       | Deployment pod host aliases                                                                                                           | `[]`                                                   |
| `configsvr.mongodbExtraFlags`                                 | MongoDB&reg; additional command line flags                                                                                            | `[]`                                                   |
| `configsvr.topologySpreadConstraints`                         | Topology Spread Constraints for pod assignment spread across your cluster among failure-domains. Evaluated as a template              | `[]`                                                   |
| `configsvr.priorityClassName`                                 | Pod priority class name                                                                                                               | `""`                                                   |
| `configsvr.podAffinityPreset`                                 | Config Server Pod affinity preset. Ignored if `affinity` is set. Allowed values: `soft` or `hard`                                     | `""`                                                   |
| `configsvr.podAntiAffinityPreset`                             | Config Server Pod anti-affinity preset. Ignored if `affinity` is set. Allowed values: `soft` or `hard`                                | `soft`                                                 |
| `configsvr.nodeAffinityPreset.type`                           | Config Server Node affinity preset type. Ignored if `affinity` is set. Allowed values: `soft` or `hard`                               | `""`                                                   |
| `configsvr.nodeAffinityPreset.key`                            | Config Server Node label key to match Ignored if `affinity` is set.                                                                   | `""`                                                   |
| `configsvr.nodeAffinityPreset.values`                         | Config Server Node label values to match. Ignored if `affinity` is set.                                                               | `[]`                                                   |
| `configsvr.affinity`                                          | Config Server Affinity for pod assignment                                                                                             | `{}`                                                   |
| `configsvr.nodeSelector`                                      | Config Server Node labels for pod assignment                                                                                          | `{}`                                                   |
| `configsvr.tolerations`                                       | Config Server Tolerations for pod assignment                                                                                          | `[]`                                                   |
| `configsvr.podManagementPolicy`                               | Statefulset's pod management policy, allows parallel startup of pods                                                                  | `OrderedReady`                                         |
| `configsvr.updateStrategy.type`                               | updateStrategy for MongoDB&reg; Primary, Secondary and Arbiter statefulsets                                                           | `RollingUpdate`                                        |
| `configsvr.config`                                            | MongoDB&reg; configuration file                                                                                                       | `""`                                                   |
| `configsvr.configCM`                                          | ConfigMap name with Config Server configuration file (cannot be used with configsvr.config)                                           | `""`                                                   |
| `configsvr.extraEnvVars`                                      | An array to add extra env vars                                                                                                        | `[]`                                                   |
| `configsvr.extraEnvVarsCM`                                    | Name of a ConfigMap containing extra env vars                                                                                         | `""`                                                   |
| `configsvr.extraEnvVarsSecret`                                | Name of a Secret containing extra env vars                                                                                            | `""`                                                   |
| `configsvr.sidecars`                                          | Add sidecars to the pod                                                                                                               | `[]`                                                   |
| `configsvr.initContainers`                                    | Add init containers to the pod                                                                                                        | `[]`                                                   |
| `configsvr.podAnnotations`                                    | Additional pod annotations                                                                                                            | `{}`                                                   |
| `configsvr.podLabels`                                         | Additional pod labels                                                                                                                 | `{}`                                                   |
| `configsvr.extraVolumes`                                      | Array to add extra volumes. Requires setting `extraVolumeMounts`                                                                      | `[]`                                                   |
| `configsvr.extraVolumeMounts`                                 | Array to add extra mounts (normally used with extraVolumes). Normally used with `extraVolumes`                                        | `[]`                                                   |
| `configsvr.schedulerName`                                     | Use an alternate scheduler, e.g. "stork".                                                                                             | `""`                                                   |
| `configsvr.pdb.create`                                        | Enable pod disruption budget                                                                                                          | `false`                                                |
| `configsvr.pdb.minAvailable`                                  | Minimum number of available config pods allowed (`0` to disable)                                                                      | `0`                                                    |
| `configsvr.pdb.maxUnavailable`                                | Maximum number of unavailable config pods allowed (`0` to disable)                                                                    | `1`                                                    |
| `configsvr.persistence.enabled`                               | Use a PVC to persist data                                                                                                             | `true`                                                 |
| `configsvr.persistence.mountPath`                             | Path to mount the volume at                                                                                                           | `/bitnami/mongodb`                                     |
| `configsvr.persistence.subPath`                               | Subdirectory of the volume to mount at (evaluated as a template)                                                                      | `""`                                                   |
| `configsvr.persistence.storageClass`                          | Storage class of backing PVC                                                                                                          | `""`                                                   |
| `configsvr.persistence.accessModes`                           | Use volume as ReadOnly or ReadWrite                                                                                                   | `["ReadWriteOnce"]`                                    |
| `configsvr.persistence.size`                                  | PersistentVolumeClaim size                                                                                                            | `8Gi`                                                  |
| `configsvr.persistence.annotations`                           | Persistent Volume annotations                                                                                                         | `{}`                                                   |
| `configsvr.persistence.resourcePolicy`                        | Setting it to "keep" to avoid removing PVCs during a helm delete operation. Leaving it empty will delete PVCs after the chart deleted | `""`                                                   |
| `configsvr.serviceAccount.create`                             | Specifies whether a ServiceAccount should be created for Config Server                                                                | `false`                                                |
| `configsvr.serviceAccount.name`                               | Name of a Service Account to be used by Config Server                                                                                 | `""`                                                   |
| `configsvr.serviceAccount.annotations`                        | Additional Service Account annotations (evaluated as a template)                                                                      | `{}`                                                   |
| `configsvr.serviceAccount.automountServiceAccountToken`       | Automount service account token for the server service account                                                                        | `true`                                                 |
| `configsvr.external.host`                                     | Primary node of an external Config Server replicaset                                                                                  | `""`                                                   |
| `configsvr.external.rootPassword`                             | Root password of the external Config Server replicaset                                                                                | `""`                                                   |
| `configsvr.external.replicasetName`                           | Replicaset name of an external Config Server                                                                                          | `""`                                                   |
| `configsvr.external.replicasetKey`                            | Replicaset key of an external Config Server                                                                                           | `""`                                                   |
| `configsvr.podSecurityContext.enabled`                        | Enable security context                                                                                                               | `true`                                                 |
| `configsvr.podSecurityContext.fsGroup`                        | Group ID for the container                                                                                                            | `1001`                                                 |
| `configsvr.containerSecurityContext.enabled`                  | Enabled containers' Security Context                                                                                                  | `true`                                                 |
| `configsvr.containerSecurityContext.runAsUser`                | Set containers' Security Context runAsUser                                                                                            | `1001`                                                 |
| `configsvr.containerSecurityContext.runAsNonRoot`             | Set container's Security Context runAsNonRoot                                                                                         | `true`                                                 |
| `configsvr.containerSecurityContext.privileged`               | Set container's Security Context privileged                                                                                           | `false`                                                |
| `configsvr.containerSecurityContext.readOnlyRootFilesystem`   | Set container's Security Context readOnlyRootFilesystem                                                                               | `false`                                                |
| `configsvr.containerSecurityContext.allowPrivilegeEscalation` | Set container's Security Context allowPrivilegeEscalation                                                                             | `false`                                                |
| `configsvr.containerSecurityContext.capabilities.drop`        | List of capabilities to be dropped                                                                                                    | `["ALL"]`                                              |
| `configsvr.containerSecurityContext.seccompProfile.type`      | Set container's Security Context seccomp profile                                                                                      | `RuntimeDefault`                                       |
| `configsvr.command`                                           | Override default container command (useful when using custom images)                                                                  | `["/bin/bash","/entrypoint/replicaset-entrypoint.sh"]` |
| `configsvr.args`                                              | Override default container args (useful when using custom images)                                                                     | `[]`                                                   |
| `configsvr.terminationGracePeriodSeconds`                     | Seconds Redmine pod needs to terminate gracefully                                                                                     | `""`                                                   |
| `configsvr.lifecycleHooks`                                    | for the Config Server container(s) to automate configuration before or after startup                                                  | `{}`                                                   |
| `configsvr.livenessProbe.enabled`                             | Enable livenessProbe                                                                                                                  | `true`                                                 |
| `configsvr.livenessProbe.initialDelaySeconds`                 | Initial delay seconds for livenessProbe                                                                                               | `60`                                                   |
| `configsvr.livenessProbe.periodSeconds`                       | Period seconds for livenessProbe                                                                                                      | `30`                                                   |
| `configsvr.livenessProbe.timeoutSeconds`                      | Timeout seconds for livenessProbe                                                                                                     | `20`                                                   |
| `configsvr.livenessProbe.failureThreshold`                    | Failure threshold for livenessProbe                                                                                                   | `2`                                                    |
| `configsvr.livenessProbe.successThreshold`                    | Success threshold for livenessProbe                                                                                                   | `1`                                                    |
| `configsvr.readinessProbe.enabled`                            | Enable readinessProbe                                                                                                                 | `true`                                                 |
| `configsvr.readinessProbe.initialDelaySeconds`                | Initial delay seconds for readinessProbe                                                                                              | `10`                                                   |
| `configsvr.readinessProbe.periodSeconds`                      | Period seconds for readinessProbe                                                                                                     | `30`                                                   |
| `configsvr.readinessProbe.timeoutSeconds`                     | Timeout seconds for readinessProbe                                                                                                    | `20`                                                   |
| `configsvr.readinessProbe.failureThreshold`                   | Failure threshold for readinessProbe                                                                                                  | `6`                                                    |
| `configsvr.readinessProbe.successThreshold`                   | Success threshold for readinessProbe                                                                                                  | `1`                                                    |
| `configsvr.startupProbe.enabled`                              | Enable startupProbe                                                                                                                   | `true`                                                 |
| `configsvr.startupProbe.initialDelaySeconds`                  | Initial delay seconds for startupProbe                                                                                                | `0`                                                    |
| `configsvr.startupProbe.periodSeconds`                        | Period seconds for startupProbe                                                                                                       | `10`                                                   |
| `configsvr.startupProbe.timeoutSeconds`                       | Timeout seconds for startupProbe                                                                                                      | `5`                                                    |
| `configsvr.startupProbe.failureThreshold`                     | Failure threshold for startupProbe                                                                                                    | `30`                                                   |
| `configsvr.startupProbe.successThreshold`                     | Success threshold for startupProbe                                                                                                    | `1`                                                    |
| `configsvr.customLivenessProbe`                               | Custom livenessProbe that overrides the default one                                                                                   | `{}`                                                   |
| `configsvr.customReadinessProbe`                              | Custom readinessProbe that overrides the default one                                                                                  | `{}`                                                   |
| `configsvr.customStartupProbe`                                | Custom startupProbe that overrides the default one                                                                                    | `{}`                                                   |

### Mongos parameters

| Name                                                       | Description                                                                                                                  | Value            |
| ---------------------------------------------------------- | ---------------------------------------------------------------------------------------------------------------------------- | ---------------- |
| `mongos.replicaCount`                                      | Number of replicas                                                                                                           | `1`              |
| `mongos.resources`                                         | Configure pod resources                                                                                                      | `{}`             |
| `mongos.hostAliases`                                       | Deployment pod host aliases                                                                                                  | `[]`             |
| `mongos.mongodbExtraFlags`                                 | MongoDB&reg; additional command line flags                                                                                   | `[]`             |
| `mongos.topologySpreadConstraints`                         | Topology Spread Constraints for pod assignment spread across your cluster among failure-domains. Evaluated as a template     | `[]`             |
| `mongos.priorityClassName`                                 | Pod priority class name                                                                                                      | `""`             |
| `mongos.podAffinityPreset`                                 | Mongos Pod affinity preset. Ignored if `affinity` is set. Allowed values: `soft` or `hard`                                   | `""`             |
| `mongos.podAntiAffinityPreset`                             | Mongos Pod anti-affinity preset. Ignored if `affinity` is set. Allowed values: `soft` or `hard`                              | `soft`           |
| `mongos.nodeAffinityPreset.type`                           | Mongos Node affinity preset type. Ignored if `affinity` is set. Allowed values: `soft` or `hard`                             | `""`             |
| `mongos.nodeAffinityPreset.key`                            | Mongos Node label key to match Ignored if `affinity` is set.                                                                 | `""`             |
| `mongos.nodeAffinityPreset.values`                         | Mongos Node label values to match. Ignored if `affinity` is set.                                                             | `[]`             |
| `mongos.affinity`                                          | Mongos Affinity for pod assignment                                                                                           | `{}`             |
| `mongos.nodeSelector`                                      | Mongos Node labels for pod assignment                                                                                        | `{}`             |
| `mongos.tolerations`                                       | Mongos Tolerations for pod assignment                                                                                        | `[]`             |
| `mongos.podManagementPolicy`                               | Statefulsets pod management policy, allows parallel startup of pods                                                          | `OrderedReady`   |
| `mongos.updateStrategy.type`                               | updateStrategy for MongoDB&reg; Primary, Secondary and Arbiter statefulsets                                                  | `RollingUpdate`  |
| `mongos.config`                                            | MongoDB&reg; configuration file                                                                                              | `""`             |
| `mongos.configCM`                                          | ConfigMap name with MongoDB&reg; configuration file (cannot be used with mongos.config)                                      | `""`             |
| `mongos.extraEnvVars`                                      | An array to add extra env vars                                                                                               | `[]`             |
| `mongos.extraEnvVarsCM`                                    | Name of a ConfigMap containing extra env vars                                                                                | `""`             |
| `mongos.extraEnvVarsSecret`                                | Name of a Secret containing extra env vars                                                                                   | `""`             |
| `mongos.sidecars`                                          | Add sidecars to the pod                                                                                                      | `[]`             |
| `mongos.initContainers`                                    | Add init containers to the pod                                                                                               | `[]`             |
| `mongos.podAnnotations`                                    | Additional pod annotations                                                                                                   | `{}`             |
| `mongos.podLabels`                                         | Additional pod labels                                                                                                        | `{}`             |
| `mongos.extraVolumes`                                      | Array to add extra volumes. Requires setting `extraVolumeMounts`                                                             | `[]`             |
| `mongos.extraVolumeMounts`                                 | Array to add extra volume mounts. Normally used with `extraVolumes`.                                                         | `[]`             |
| `mongos.schedulerName`                                     | Use an alternate scheduler, e.g. "stork".                                                                                    | `""`             |
| `mongos.useStatefulSet`                                    | Use StatefulSet instead of Deployment                                                                                        | `false`          |
| `mongos.servicePerReplica.enabled`                         | Create one service per mongos replica (must be used with statefulset)                                                        | `false`          |
| `mongos.servicePerReplica.annotations`                     | Additional service annotations (evaluate as a template)                                                                      | `{}`             |
| `mongos.servicePerReplica.type`                            | Service type                                                                                                                 | `ClusterIP`      |
| `mongos.servicePerReplica.externalTrafficPolicy`           | External traffic policy                                                                                                      | `Cluster`        |
| `mongos.servicePerReplica.port`                            | MongoDB&reg; service port                                                                                                    | `27017`          |
| `mongos.servicePerReplica.clusterIPs`                      | Array of static clusterIPs for each MongoDB@reg; replica. Length must be the same as mongos.replicaCount                     | `[]`             |
| `mongos.servicePerReplica.nodePorts`                       | Array of node ports used for each MongoDB@reg; replica. Length must be the same as mongos.replicaCount                       | `[]`             |
| `mongos.servicePerReplica.externalIPs`                     | External IP list to use with ClusterIP service type                                                                          | `[]`             |
| `mongos.servicePerReplica.loadBalancerIPs`                 | Array of static IP Address to use for each replica LoadBalancer service type. Length must be the same as mongos.replicaCount | `[]`             |
| `mongos.servicePerReplica.loadBalancerSourceRanges`        | List of IP ranges allowed access to load balancer (if supported)                                                             | `[]`             |
| `mongos.servicePerReplica.extraPorts`                      | Extra ports to expose (normally used with the `sidecar` value)                                                               | `[]`             |
| `mongos.servicePerReplica.sessionAffinity`                 | Session Affinity for Kubernetes service, can be "None" or "ClientIP"                                                         | `None`           |
| `mongos.servicePerReplica.sessionAffinityConfig`           | Additional settings for the sessionAffinity                                                                                  | `{}`             |
| `mongos.pdb.create`                                        | Enable pod disruption budget                                                                                                 | `false`          |
| `mongos.pdb.minAvailable`                                  | Minimum number of available mongo pods allowed (`0` to disable)                                                              | `0`              |
| `mongos.pdb.maxUnavailable`                                | Maximum number of unavailable mongo pods allowed (`0` to disable)                                                            | `1`              |
| `mongos.serviceAccount.create`                             | Whether to create a Service Account for mongos automatically                                                                 | `false`          |
| `mongos.serviceAccount.name`                               | Name of a Service Account to be used by mongos                                                                               | `""`             |
| `mongos.serviceAccount.annotations`                        | Additional Service Account annotations (evaluated as a template)                                                             | `{}`             |
| `mongos.serviceAccount.automountServiceAccountToken`       | Automount service account token for the server service account                                                               | `true`           |
| `mongos.podSecurityContext.enabled`                        | Enable security context                                                                                                      | `true`           |
| `mongos.podSecurityContext.fsGroup`                        | Group ID for the container                                                                                                   | `1001`           |
| `mongos.containerSecurityContext.enabled`                  | Enabled containers' Security Context                                                                                         | `true`           |
| `mongos.containerSecurityContext.runAsUser`                | Set containers' Security Context runAsUser                                                                                   | `1001`           |
| `mongos.containerSecurityContext.runAsNonRoot`             | Set container's Security Context runAsNonRoot                                                                                | `true`           |
| `mongos.containerSecurityContext.privileged`               | Set container's Security Context privileged                                                                                  | `false`          |
| `mongos.containerSecurityContext.readOnlyRootFilesystem`   | Set container's Security Context readOnlyRootFilesystem                                                                      | `false`          |
| `mongos.containerSecurityContext.allowPrivilegeEscalation` | Set container's Security Context allowPrivilegeEscalation                                                                    | `false`          |
| `mongos.containerSecurityContext.capabilities.drop`        | List of capabilities to be dropped                                                                                           | `["ALL"]`        |
| `mongos.containerSecurityContext.seccompProfile.type`      | Set container's Security Context seccomp profile                                                                             | `RuntimeDefault` |
| `mongos.command`                                           | Override default container command (useful when using custom images)                                                         | `[]`             |
| `mongos.args`                                              | Override default container args (useful when using custom images)                                                            | `[]`             |
| `mongos.terminationGracePeriodSeconds`                     | Seconds Redmine pod needs to terminate gracefully                                                                            | `""`             |
| `mongos.lifecycleHooks`                                    | for the Mongo container(s) to automate configuration before or after startup                                                 | `{}`             |
| `mongos.livenessProbe.enabled`                             | Enable livenessProbe                                                                                                         | `true`           |
| `mongos.livenessProbe.initialDelaySeconds`                 | Initial delay seconds for livenessProbe                                                                                      | `60`             |
| `mongos.livenessProbe.periodSeconds`                       | Period seconds for livenessProbe                                                                                             | `30`             |
| `mongos.livenessProbe.timeoutSeconds`                      | Timeout seconds for livenessProbe                                                                                            | `20`             |
| `mongos.livenessProbe.failureThreshold`                    | Failure threshold for livenessProbe                                                                                          | `2`              |
| `mongos.livenessProbe.successThreshold`                    | Success threshold for livenessProbe                                                                                          | `1`              |
| `mongos.readinessProbe.enabled`                            | Enable readinessProbe                                                                                                        | `true`           |
| `mongos.readinessProbe.initialDelaySeconds`                | Initial delay seconds for readinessProbe                                                                                     | `10`             |
| `mongos.readinessProbe.periodSeconds`                      | Period seconds for readinessProbe                                                                                            | `30`             |
| `mongos.readinessProbe.timeoutSeconds`                     | Timeout seconds for readinessProbe                                                                                           | `20`             |
| `mongos.readinessProbe.failureThreshold`                   | Failure threshold for readinessProbe                                                                                         | `6`              |
| `mongos.readinessProbe.successThreshold`                   | Success threshold for readinessProbe                                                                                         | `1`              |
| `mongos.startupProbe.enabled`                              | Enable startupProbe                                                                                                          | `false`          |
| `mongos.startupProbe.initialDelaySeconds`                  | Initial delay seconds for startupProbe                                                                                       | `0`              |
| `mongos.startupProbe.periodSeconds`                        | Period seconds for startupProbe                                                                                              | `10`             |
| `mongos.startupProbe.timeoutSeconds`                       | Timeout seconds for startupProbe                                                                                             | `5`              |
| `mongos.startupProbe.failureThreshold`                     | Failure threshold for startupProbe                                                                                           | `30`             |
| `mongos.startupProbe.successThreshold`                     | Success threshold for startupProbe                                                                                           | `1`              |
| `mongos.customLivenessProbe`                               | Custom livenessProbe that overrides the default one                                                                          | `{}`             |
| `mongos.customReadinessProbe`                              | Custom readinessProbe that overrides the default one                                                                         | `{}`             |
| `mongos.customStartupProbe`                                | Custom startupProbe that overrides the default one                                                                           | `{}`             |

### Shard configuration: Data node parameters

| Name                                                                  | Description                                                                                                              | Value                                                  |
| --------------------------------------------------------------------- | ------------------------------------------------------------------------------------------------------------------------ | ------------------------------------------------------ |
| `shardsvr.dataNode.replicaCount`                                      | Number of nodes in each shard replica set (the first node will be primary)                                               | `1`                                                    |
| `shardsvr.dataNode.resources`                                         | Configure pod resources                                                                                                  | `{}`                                                   |
| `shardsvr.dataNode.mongodbExtraFlags`                                 | MongoDB&reg; additional command line flags                                                                               | `[]`                                                   |
| `shardsvr.dataNode.topologySpreadConstraints`                         | Topology Spread Constraints for pod assignment spread across your cluster among failure-domains. Evaluated as a template | `[]`                                                   |
| `shardsvr.dataNode.priorityClassName`                                 | Pod priority class name                                                                                                  | `""`                                                   |
| `shardsvr.dataNode.podAffinityPreset`                                 | Data nodes Pod affinity preset. Ignored if `affinity` is set. Allowed values: `soft` or `hard`                           | `""`                                                   |
| `shardsvr.dataNode.podAntiAffinityPreset`                             | Data nodes Pod anti-affinity preset. Ignored if `affinity` is set. Allowed values: `soft` or `hard`                      | `soft`                                                 |
| `shardsvr.dataNode.nodeAffinityPreset.type`                           | Data nodes Node affinity preset type. Ignored if `affinity` is set. Allowed values: `soft` or `hard`                     | `""`                                                   |
| `shardsvr.dataNode.nodeAffinityPreset.key`                            | Data nodes Node label key to match Ignored if `affinity` is set.                                                         | `""`                                                   |
| `shardsvr.dataNode.nodeAffinityPreset.values`                         | Data nodes Node label values to match. Ignored if `affinity` is set.                                                     | `[]`                                                   |
| `shardsvr.dataNode.affinity`                                          | Data nodes Affinity for pod assignment                                                                                   | `{}`                                                   |
| `shardsvr.dataNode.nodeSelector`                                      | Data nodes Node labels for pod assignment                                                                                | `{}`                                                   |
| `shardsvr.dataNode.tolerations`                                       | Data nodes Tolerations for pod assignment                                                                                | `[]`                                                   |
| `shardsvr.dataNode.podManagementPolicy`                               | podManagementPolicy for the statefulset, allows parallel startup of pods                                                 | `OrderedReady`                                         |
| `shardsvr.dataNode.updateStrategy.type`                               | updateStrategy for MongoDB&reg; Primary, Secondary and Arbiter statefulsets                                              | `RollingUpdate`                                        |
| `shardsvr.dataNode.hostAliases`                                       | Deployment pod host aliases                                                                                              | `[]`                                                   |
| `shardsvr.dataNode.config`                                            | Entries for the MongoDB&reg; config file                                                                                 | `""`                                                   |
| `shardsvr.dataNode.configCM`                                          | ConfigMap name with MongoDB&reg; configuration (cannot be used with shardsvr.dataNode.config)                            | `""`                                                   |
| `shardsvr.dataNode.extraEnvVars`                                      | An array to add extra env vars                                                                                           | `[]`                                                   |
| `shardsvr.dataNode.extraEnvVarsCM`                                    | Name of a ConfigMap containing extra env vars                                                                            | `""`                                                   |
| `shardsvr.dataNode.extraEnvVarsSecret`                                | Name of a Secret containing extra env vars                                                                               | `""`                                                   |
| `shardsvr.dataNode.sidecars`                                          | Attach additional containers (evaluated as a template)                                                                   | `[]`                                                   |
| `shardsvr.dataNode.initContainers`                                    | Add init containers to the pod                                                                                           | `[]`                                                   |
| `shardsvr.dataNode.podAnnotations`                                    | Additional pod annotations                                                                                               | `{}`                                                   |
| `shardsvr.dataNode.podLabels`                                         | Additional pod labels                                                                                                    | `{}`                                                   |
| `shardsvr.dataNode.extraVolumes`                                      | Array to add extra volumes. Requires setting `extraVolumeMounts`                                                         | `[]`                                                   |
| `shardsvr.dataNode.extraVolumeMounts`                                 | Array to add extra mounts. Normally used with `extraVolumes`                                                             | `[]`                                                   |
| `shardsvr.dataNode.schedulerName`                                     | Use an alternate scheduler, e.g. "stork".                                                                                | `""`                                                   |
| `shardsvr.dataNode.pdb.create`                                        | Enable pod disruption budget                                                                                             | `false`                                                |
| `shardsvr.dataNode.pdb.minAvailable`                                  | Minimum number of available data pods allowed (`0` to disable)                                                           | `0`                                                    |
| `shardsvr.dataNode.pdb.maxUnavailable`                                | Maximum number of unavailable data pods allowed (`0` to disable)                                                         | `1`                                                    |
| `shardsvr.dataNode.serviceAccount.create`                             | Specifies whether a ServiceAccount should be created for shardsvr                                                        | `false`                                                |
| `shardsvr.dataNode.serviceAccount.name`                               | Name of a Service Account to be used by shardsvr data pods                                                               | `""`                                                   |
| `shardsvr.dataNode.serviceAccount.annotations`                        | Additional Service Account annotations (evaluated as a template)                                                         | `{}`                                                   |
| `shardsvr.dataNode.serviceAccount.automountServiceAccountToken`       | Automount service account token for the server service account                                                           | `true`                                                 |
| `shardsvr.dataNode.podSecurityContext.enabled`                        | Enable security context                                                                                                  | `true`                                                 |
| `shardsvr.dataNode.podSecurityContext.fsGroup`                        | Group ID for the container                                                                                               | `1001`                                                 |
| `shardsvr.dataNode.containerSecurityContext.enabled`                  | Enabled containers' Security Context                                                                                     | `true`                                                 |
| `shardsvr.dataNode.containerSecurityContext.runAsUser`                | Set containers' Security Context runAsUser                                                                               | `1001`                                                 |
| `shardsvr.dataNode.containerSecurityContext.runAsNonRoot`             | Set container's Security Context runAsNonRoot                                                                            | `true`                                                 |
| `shardsvr.dataNode.containerSecurityContext.privileged`               | Set container's Security Context privileged                                                                              | `false`                                                |
| `shardsvr.dataNode.containerSecurityContext.readOnlyRootFilesystem`   | Set container's Security Context readOnlyRootFilesystem                                                                  | `false`                                                |
| `shardsvr.dataNode.containerSecurityContext.allowPrivilegeEscalation` | Set container's Security Context allowPrivilegeEscalation                                                                | `false`                                                |
| `shardsvr.dataNode.containerSecurityContext.capabilities.drop`        | List of capabilities to be dropped                                                                                       | `["ALL"]`                                              |
| `shardsvr.dataNode.containerSecurityContext.seccompProfile.type`      | Set container's Security Context seccomp profile                                                                         | `RuntimeDefault`                                       |
| `shardsvr.dataNode.command`                                           | Override default container command (useful when using custom images)                                                     | `["/bin/bash","/entrypoint/replicaset-entrypoint.sh"]` |
| `shardsvr.dataNode.args`                                              | Override default container args (useful when using custom images)                                                        | `[]`                                                   |
| `shardsvr.dataNode.terminationGracePeriodSeconds`                     | Seconds Redmine pod needs to terminate gracefully                                                                        | `""`                                                   |
| `shardsvr.dataNode.lifecycleHooks`                                    | for the Data container(s) to automate configuration before or after startup                                              | `{}`                                                   |
| `shardsvr.dataNode.livenessProbe.enabled`                             | Enable livenessProbe                                                                                                     | `true`                                                 |
| `shardsvr.dataNode.livenessProbe.initialDelaySeconds`                 | Initial delay seconds for livenessProbe                                                                                  | `60`                                                   |
| `shardsvr.dataNode.livenessProbe.periodSeconds`                       | Period seconds for livenessProbe                                                                                         | `30`                                                   |
| `shardsvr.dataNode.livenessProbe.timeoutSeconds`                      | Timeout seconds for livenessProbe                                                                                        | `20`                                                   |
| `shardsvr.dataNode.livenessProbe.failureThreshold`                    | Failure threshold for livenessProbe                                                                                      | `2`                                                    |
| `shardsvr.dataNode.livenessProbe.successThreshold`                    | Success threshold for livenessProbe                                                                                      | `1`                                                    |
| `shardsvr.dataNode.readinessProbe.enabled`                            | Enable readinessProbe                                                                                                    | `true`                                                 |
| `shardsvr.dataNode.readinessProbe.initialDelaySeconds`                | Initial delay seconds for readinessProbe                                                                                 | `10`                                                   |
| `shardsvr.dataNode.readinessProbe.periodSeconds`                      | Period seconds for readinessProbe                                                                                        | `30`                                                   |
| `shardsvr.dataNode.readinessProbe.timeoutSeconds`                     | Timeout seconds for readinessProbe                                                                                       | `20`                                                   |
| `shardsvr.dataNode.readinessProbe.failureThreshold`                   | Failure threshold for readinessProbe                                                                                     | `6`                                                    |
| `shardsvr.dataNode.readinessProbe.successThreshold`                   | Success threshold for readinessProbe                                                                                     | `1`                                                    |
| `shardsvr.dataNode.startupProbe.enabled`                              | Enable startupProbe                                                                                                      | `false`                                                |
| `shardsvr.dataNode.startupProbe.initialDelaySeconds`                  | Initial delay seconds for startupProbe                                                                                   | `0`                                                    |
| `shardsvr.dataNode.startupProbe.periodSeconds`                        | Period seconds for startupProbe                                                                                          | `10`                                                   |
| `shardsvr.dataNode.startupProbe.timeoutSeconds`                       | Timeout seconds for startupProbe                                                                                         | `5`                                                    |
| `shardsvr.dataNode.startupProbe.failureThreshold`                     | Failure threshold for startupProbe                                                                                       | `30`                                                   |
| `shardsvr.dataNode.startupProbe.successThreshold`                     | Success threshold for startupProbe                                                                                       | `1`                                                    |
| `shardsvr.dataNode.customLivenessProbe`                               | Custom livenessProbe that overrides the default one                                                                      | `{}`                                                   |
| `shardsvr.dataNode.customReadinessProbe`                              | Custom readinessProbe that overrides the default one                                                                     | `{}`                                                   |
| `shardsvr.dataNode.customStartupProbe`                                | Custom startupProbe that overrides the default one                                                                       | `{}`                                                   |

### Shard configuration: Persistence parameters

| Name                                  | Description                                                                                                                           | Value               |
| ------------------------------------- | ------------------------------------------------------------------------------------------------------------------------------------- | ------------------- |
| `shardsvr.persistence.enabled`        | Use a PVC to persist data                                                                                                             | `true`              |
| `shardsvr.persistence.mountPath`      | The path the volume will be mounted at, useful when using different MongoDB&reg; images.                                              | `/bitnami/mongodb`  |
| `shardsvr.persistence.subPath`        | Subdirectory of the volume to mount at (evaluated as a template)                                                                      | `""`                |
| `shardsvr.persistence.storageClass`   | Storage class of backing PVC                                                                                                          | `""`                |
| `shardsvr.persistence.accessModes`    | Use volume as ReadOnly or ReadWrite                                                                                                   | `["ReadWriteOnce"]` |
| `shardsvr.persistence.size`           | PersistentVolumeClaim size                                                                                                            | `8Gi`               |
| `shardsvr.persistence.annotations`    | Additional volume annotations                                                                                                         | `{}`                |
| `shardsvr.persistence.resourcePolicy` | Setting it to "keep" to avoid removing PVCs during a helm delete operation. Leaving it empty will delete PVCs after the chart deleted | `""`                |

### Shard configuration: Arbiter parameters

| Name                                                                 | Description                                                                                                              | Value            |
| -------------------------------------------------------------------- | ------------------------------------------------------------------------------------------------------------------------ | ---------------- |
| `shardsvr.arbiter.replicaCount`                                      | Number of arbiters in each shard replica set (the first node will be primary)                                            | `0`              |
| `shardsvr.arbiter.hostAliases`                                       | Deployment pod host aliases                                                                                              | `[]`             |
| `shardsvr.arbiter.resources`                                         | Configure pod resources                                                                                                  | `{}`             |
| `shardsvr.arbiter.mongodbExtraFlags`                                 | MongoDB&reg; additional command line flags                                                                               | `[]`             |
| `shardsvr.arbiter.topologySpreadConstraints`                         | Topology Spread Constraints for pod assignment spread across your cluster among failure-domains. Evaluated as a template | `[]`             |
| `shardsvr.arbiter.priorityClassName`                                 | Pod priority class name                                                                                                  | `""`             |
| `shardsvr.arbiter.podAffinityPreset`                                 | Arbiter's Pod affinity preset. Ignored if `affinity` is set. Allowed values: `soft` or `hard`                            | `""`             |
| `shardsvr.arbiter.podAntiAffinityPreset`                             | Arbiter's Pod anti-affinity preset. Ignored if `affinity` is set. Allowed values: `soft` or `hard`                       | `soft`           |
| `shardsvr.arbiter.nodeAffinityPreset.type`                           | Arbiter's Node affinity preset type. Ignored if `affinity` is set. Allowed values: `soft` or `hard`                      | `""`             |
| `shardsvr.arbiter.nodeAffinityPreset.key`                            | Arbiter's Node label key to match Ignored if `affinity` is set.                                                          | `""`             |
| `shardsvr.arbiter.nodeAffinityPreset.values`                         | Arbiter's Node label values to match. Ignored if `affinity` is set.                                                      | `[]`             |
| `shardsvr.arbiter.affinity`                                          | Arbiter's Affinity for pod assignment                                                                                    | `{}`             |
| `shardsvr.arbiter.nodeSelector`                                      | Arbiter's Node labels for pod assignment                                                                                 | `{}`             |
| `shardsvr.arbiter.tolerations`                                       | Arbiter's Tolerations for pod assignment                                                                                 | `[]`             |
| `shardsvr.arbiter.podManagementPolicy`                               | Statefulset's pod management policy, allows parallel startup of pods                                                     | `OrderedReady`   |
| `shardsvr.arbiter.updateStrategy.type`                               | updateStrategy for MongoDB&reg; Primary, Secondary and Arbiter statefulsets                                              | `RollingUpdate`  |
| `shardsvr.arbiter.config`                                            | MongoDB&reg; configuration file                                                                                          | `""`             |
| `shardsvr.arbiter.configCM`                                          | ConfigMap name with MongoDB&reg; configuration file (cannot be used with shardsvr.arbiter.config)                        | `""`             |
| `shardsvr.arbiter.extraEnvVars`                                      | An array to add extra env vars                                                                                           | `[]`             |
| `shardsvr.arbiter.extraEnvVarsCM`                                    | Name of a ConfigMap containing extra env vars                                                                            | `""`             |
| `shardsvr.arbiter.extraEnvVarsSecret`                                | Name of a Secret containing extra env vars                                                                               | `""`             |
| `shardsvr.arbiter.sidecars`                                          | Add sidecars to the pod                                                                                                  | `[]`             |
| `shardsvr.arbiter.initContainers`                                    | Add init containers to the pod                                                                                           | `[]`             |
| `shardsvr.arbiter.podAnnotations`                                    | Additional pod annotations                                                                                               | `{}`             |
| `shardsvr.arbiter.podLabels`                                         | Additional pod labels                                                                                                    | `{}`             |
| `shardsvr.arbiter.extraVolumes`                                      | Array to add extra volumes                                                                                               | `[]`             |
| `shardsvr.arbiter.extraVolumeMounts`                                 | Array to add extra mounts (normally used with extraVolumes)                                                              | `[]`             |
| `shardsvr.arbiter.schedulerName`                                     | Use an alternate scheduler, e.g. "stork".                                                                                | `""`             |
| `shardsvr.arbiter.serviceAccount.create`                             | Specifies whether a ServiceAccount should be created for shardsvr arbiter nodes                                          | `false`          |
| `shardsvr.arbiter.serviceAccount.name`                               | Name of a Service Account to be used by shardsvr arbiter pods                                                            | `""`             |
| `shardsvr.arbiter.serviceAccount.annotations`                        | Additional Service Account annotations (evaluated as a template)                                                         | `{}`             |
| `shardsvr.arbiter.serviceAccount.automountServiceAccountToken`       | Automount service account token for the server service account                                                           | `true`           |
| `shardsvr.arbiter.podSecurityContext.enabled`                        | Enable security context                                                                                                  | `true`           |
| `shardsvr.arbiter.podSecurityContext.fsGroup`                        | Group ID for the container                                                                                               | `1001`           |
| `shardsvr.arbiter.containerSecurityContext.enabled`                  | Enabled containers' Security Context                                                                                     | `true`           |
| `shardsvr.arbiter.containerSecurityContext.runAsUser`                | Set containers' Security Context runAsUser                                                                               | `1001`           |
| `shardsvr.arbiter.containerSecurityContext.runAsNonRoot`             | Set container's Security Context runAsNonRoot                                                                            | `true`           |
| `shardsvr.arbiter.containerSecurityContext.privileged`               | Set container's Security Context privileged                                                                              | `false`          |
| `shardsvr.arbiter.containerSecurityContext.readOnlyRootFilesystem`   | Set container's Security Context readOnlyRootFilesystem                                                                  | `false`          |
| `shardsvr.arbiter.containerSecurityContext.allowPrivilegeEscalation` | Set container's Security Context allowPrivilegeEscalation                                                                | `false`          |
| `shardsvr.arbiter.containerSecurityContext.capabilities.drop`        | List of capabilities to be dropped                                                                                       | `["ALL"]`        |
| `shardsvr.arbiter.containerSecurityContext.seccompProfile.type`      | Set container's Security Context seccomp profile                                                                         | `RuntimeDefault` |
| `shardsvr.arbiter.command`                                           | Override default container command (useful when using custom images)                                                     | `[]`             |
| `shardsvr.arbiter.args`                                              | Override default container args (useful when using custom images)                                                        | `[]`             |
| `shardsvr.arbiter.terminationGracePeriodSeconds`                     | Seconds Redmine pod needs to terminate gracefully                                                                        | `""`             |
| `shardsvr.arbiter.lifecycleHooks`                                    | for the arbiter container(s) to automate configuration before or after startup                                           | `{}`             |
| `shardsvr.arbiter.livenessProbe.enabled`                             | Enable livenessProbe                                                                                                     | `true`           |
| `shardsvr.arbiter.livenessProbe.initialDelaySeconds`                 | Initial delay seconds for livenessProbe                                                                                  | `60`             |
| `shardsvr.arbiter.livenessProbe.periodSeconds`                       | Period seconds for livenessProbe                                                                                         | `30`             |
| `shardsvr.arbiter.livenessProbe.timeoutSeconds`                      | Timeout seconds for livenessProbe                                                                                        | `20`             |
| `shardsvr.arbiter.livenessProbe.failureThreshold`                    | Failure threshold for livenessProbe                                                                                      | `2`              |
| `shardsvr.arbiter.livenessProbe.successThreshold`                    | Success threshold for livenessProbe                                                                                      | `1`              |
| `shardsvr.arbiter.readinessProbe.enabled`                            | Enable readinessProbe                                                                                                    | `true`           |
| `shardsvr.arbiter.readinessProbe.initialDelaySeconds`                | Initial delay seconds for readinessProbe                                                                                 | `10`             |
| `shardsvr.arbiter.readinessProbe.periodSeconds`                      | Period seconds for readinessProbe                                                                                        | `30`             |
| `shardsvr.arbiter.readinessProbe.timeoutSeconds`                     | Timeout seconds for readinessProbe                                                                                       | `20`             |
| `shardsvr.arbiter.readinessProbe.failureThreshold`                   | Failure threshold for readinessProbe                                                                                     | `6`              |
| `shardsvr.arbiter.readinessProbe.successThreshold`                   | Success threshold for readinessProbe                                                                                     | `1`              |
| `shardsvr.arbiter.startupProbe.enabled`                              | Enable startupProbe                                                                                                      | `false`          |
| `shardsvr.arbiter.startupProbe.initialDelaySeconds`                  | Initial delay seconds for startupProbe                                                                                   | `0`              |
| `shardsvr.arbiter.startupProbe.periodSeconds`                        | Period seconds for startupProbe                                                                                          | `10`             |
| `shardsvr.arbiter.startupProbe.timeoutSeconds`                       | Timeout seconds for startupProbe                                                                                         | `5`              |
| `shardsvr.arbiter.startupProbe.failureThreshold`                     | Failure threshold for startupProbe                                                                                       | `30`             |
| `shardsvr.arbiter.startupProbe.successThreshold`                     | Success threshold for startupProbe                                                                                       | `1`              |
| `shardsvr.arbiter.customLivenessProbe`                               | Custom livenessProbe that overrides the default one                                                                      | `{}`             |
| `shardsvr.arbiter.customReadinessProbe`                              | Custom readinessProbe that overrides the default one                                                                     | `{}`             |
| `shardsvr.arbiter.customStartupProbe`                                | Custom startupProbe that overrides the default one                                                                       | `{}`             |

### Metrics parameters

| Name                                                        | Description                                                                                                           | Value                              |
| ----------------------------------------------------------- | --------------------------------------------------------------------------------------------------------------------- | ---------------------------------- |
| `metrics.enabled`                                           | Start a side-car prometheus exporter                                                                                  | `false`                            |
| `metrics.image.registry`                                    | MongoDB&reg; exporter image registry                                                                                  | `REGISTRY_NAME`                    |
| `metrics.image.repository`                                  | MongoDB&reg; exporter image name                                                                                      | `REPOSITORY_NAME/mongodb-exporter` |
| `metrics.image.digest`                                      | MongoDB&reg; exporter image digest in the way sha256:aa.... Please note this parameter, if set, will override the tag | `""`                               |
| `metrics.image.pullPolicy`                                  | MongoDB&reg; exporter image pull policy                                                                               | `Always`                           |
| `metrics.image.pullSecrets`                                 | MongoDB&reg; exporter image pull secrets                                                                              | `[]`                               |
| `metrics.useTLS`                                            | Whether to connect to MongoDB&reg; with TLS                                                                           | `false`                            |
| `metrics.extraArgs`                                         | String with extra arguments to the metrics exporter                                                                   | `""`                               |
| `metrics.resources`                                         | Metrics exporter resource requests and limits                                                                         | `{}`                               |
| `metrics.containerSecurityContext.enabled`                  | Enabled containers' Security Context                                                                                  | `true`                             |
| `metrics.containerSecurityContext.runAsUser`                | Set containers' Security Context runAsUser                                                                            | `1001`                             |
| `metrics.containerSecurityContext.runAsNonRoot`             | Set container's Security Context runAsNonRoot                                                                         | `true`                             |
| `metrics.containerSecurityContext.privileged`               | Set container's Security Context privileged                                                                           | `false`                            |
| `metrics.containerSecurityContext.readOnlyRootFilesystem`   | Set container's Security Context readOnlyRootFilesystem                                                               | `false`                            |
| `metrics.containerSecurityContext.allowPrivilegeEscalation` | Set container's Security Context allowPrivilegeEscalation                                                             | `false`                            |
| `metrics.containerSecurityContext.capabilities.drop`        | List of capabilities to be dropped                                                                                    | `["ALL"]`                          |
| `metrics.containerSecurityContext.seccompProfile.type`      | Set container's Security Context seccomp profile                                                                      | `RuntimeDefault`                   |
| `metrics.livenessProbe.enabled`                             | Enable livenessProbe                                                                                                  | `false`                            |
| `metrics.livenessProbe.initialDelaySeconds`                 | Initial delay seconds for livenessProbe                                                                               | `15`                               |
| `metrics.livenessProbe.periodSeconds`                       | Period seconds for livenessProbe                                                                                      | `5`                                |
| `metrics.livenessProbe.timeoutSeconds`                      | Timeout seconds for livenessProbe                                                                                     | `5`                                |
| `metrics.livenessProbe.failureThreshold`                    | Failure threshold for livenessProbe                                                                                   | `3`                                |
| `metrics.livenessProbe.successThreshold`                    | Success threshold for livenessProbe                                                                                   | `1`                                |
| `metrics.readinessProbe.enabled`                            | Enable readinessProbe                                                                                                 | `false`                            |
| `metrics.readinessProbe.initialDelaySeconds`                | Initial delay seconds for readinessProbe                                                                              | `5`                                |
| `metrics.readinessProbe.periodSeconds`                      | Period seconds for readinessProbe                                                                                     | `5`                                |
| `metrics.readinessProbe.timeoutSeconds`                     | Timeout seconds for readinessProbe                                                                                    | `1`                                |
| `metrics.readinessProbe.failureThreshold`                   | Failure threshold for readinessProbe                                                                                  | `3`                                |
| `metrics.readinessProbe.successThreshold`                   | Success threshold for readinessProbe                                                                                  | `1`                                |
| `metrics.startupProbe.enabled`                              | Enable startupProbe                                                                                                   | `false`                            |
| `metrics.startupProbe.initialDelaySeconds`                  | Initial delay seconds for startupProbe                                                                                | `0`                                |
| `metrics.startupProbe.periodSeconds`                        | Period seconds for startupProbe                                                                                       | `5`                                |
| `metrics.startupProbe.timeoutSeconds`                       | Timeout seconds for startupProbe                                                                                      | `2`                                |
| `metrics.startupProbe.failureThreshold`                     | Failure threshold for startupProbe                                                                                    | `15`                               |
| `metrics.startupProbe.successThreshold`                     | Success threshold for startupProbe                                                                                    | `1`                                |
| `metrics.customLivenessProbe`                               | Custom livenessProbe that overrides the default one                                                                   | `{}`                               |
| `metrics.customReadinessProbe`                              | Custom readinessProbe that overrides the default one                                                                  | `{}`                               |
| `metrics.customStartupProbe`                                | Custom startupProbe that overrides the default one                                                                    | `{}`                               |
| `metrics.containerPorts.metrics`                            | Port of the Prometheus metrics container                                                                              | `9216`                             |
| `metrics.podAnnotations`                                    | Metrics exporter pod Annotation                                                                                       | `{}`                               |
| `metrics.podMonitor.enabled`                                | Create PodMonitor Resource for scraping metrics using PrometheusOperator                                              | `false`                            |
| `metrics.podMonitor.namespace`                              | Namespace where podmonitor resource should be created                                                                 | `monitoring`                       |
| `metrics.podMonitor.interval`                               | Specify the interval at which metrics should be scraped                                                               | `30s`                              |
| `metrics.podMonitor.scrapeTimeout`                          | Specify the timeout after which the scrape is ended                                                                   | `""`                               |
| `metrics.podMonitor.additionalLabels`                       | Additional labels that can be used so PodMonitors will be discovered by Prometheus                                    | `{}`                               |

Specify each parameter using the `--set key=value[,key=value]` argument to `helm install`. For example,

```console
helm install my-release \
  --set shards=4,configsvr.replicaCount=3,shardsvr.dataNode.replicaCount=2 \
    oci://REGISTRY_NAME/REPOSITORY_NAME/mongodb-sharded
```

> Note: You need to substitute the placeholders `REGISTRY_NAME` and `REPOSITORY_NAME` with a reference to your Helm chart registry and repository. For example, in the case of Bitnami, you need to use `REGISTRY_NAME=registry-1.docker.io` and `REPOSITORY_NAME=bitnamicharts`.

The above command sets the number of shards to 4, the number of replicas for the config servers to 3 and number of replicas for data nodes to 2.

Alternatively, a YAML file that specifies the values for the parameters can be provided while installing the chart. For example,

```console
helm install my-release -f values.yaml oci://REGISTRY_NAME/REPOSITORY_NAME/mongodb-sharded
```

> Note: You need to substitute the placeholders `REGISTRY_NAME` and `REPOSITORY_NAME` with a reference to your Helm chart registry and repository. For example, in the case of Bitnami, you need to use `REGISTRY_NAME=registry-1.docker.io` and `REPOSITORY_NAME=bitnamicharts`.
> **Tip**: You can use the default [values.yaml](values.yaml)

## Configuration and installation details

### [Rolling VS Immutable tags](https://docs.bitnami.com/containers/how-to/understand-rolling-tags-containers/)

It is strongly recommended to use immutable tags in a production environment. This ensures your deployment does not change automatically if the same tag is updated with a different image.

Bitnami will release a new chart updating its containers if a new version of the main container, significant changes, or critical vulnerabilities exist.

### Change MongoDB&reg; version

To modify the MongoDB&reg; version used in this chart you can specify a [valid image tag](https://hub.docker.com/r/bitnami/mongodb-sharded/tags/) using the `image.tag` parameter. For example, `image.tag=X.Y.Z`. This approach is also applicable to other images like exporters.

### Sharding

This chart deploys a sharded cluster by default. Some characteristics of this chart are:

- It allows HA by enabling replication on the shards and the config servers. The mongos instances can be scaled horizontally as well.
- The number of secondary and arbiter nodes can be scaled out independently.

### Initialize a fresh instance

The [Bitnami MongoDB&reg;](https://github.com/bitnami/containers/tree/main/bitnami/mongodb-sharded) image allows you to use your custom scripts to initialize a fresh instance. You can create a custom config map and give it via `initScriptsCM`(check options for more details).

The allowed extensions are `.sh`, and `.js`.

### Sidecars and Init Containers

If you have a need for additional containers to run within the same pod as Kibana (e.g. an additional metrics or logging exporter), you can do so via the `sidecars` config parameter (available in the `mongos`, `shardsvr.dataNode`, `shardsvr.arbiter`, `configsvr` and `common` sections). Simply define your container according to the Kubernetes container spec.

```yaml
sidecars:
- name: your-image-name
  image: your-image
  imagePullPolicy: Always
  ports:
  - name: portname
    containerPort: 1234
```

Similarly, you can add extra init containers using the `initContainers` parameter.

```yaml
initContainers:
- name: your-image-name
  image: your-image
  imagePullPolicy: Always
  ports:
  - name: portname
    containerPort: 1234
```

### Adding extra environment variables

In case you want to add extra environment variables (useful for advanced operations like custom init scripts), you can use the `extraEnvVars` (available in the `mongos`, `shardsvr.dataNode`, `shardsvr.arbiter`, `configsvr` and `common` sections) property.

```yaml
extraEnvVars:
  - name: MONGODB_VERSION
    value: 4.0
```

Alternatively, you can use a ConfigMap or a Secret with the environment variables. To do so, use the `extraEnvVarsCM` or the `extraEnvVarsSecret` values.

### Using an external config server

It is possible to not deploy any shards or a config server. For example, it is possible to simply deploy `mongos` instances that point to an external MongoDB&reg; sharded database. If that is the case, set the `configsvr.external.host` and `configsvr.external.replicasetName` for the mongos instances to connect. For authentication, set the `configsvr.external.rootPassword` and `configsvr.external.replicasetKey` values.

## Persistence

The [Bitnami MongoDB&reg;](https://github.com/bitnami/containers/tree/main/bitnami/mongodb-sharded) image stores the MongoDB&reg; data and configurations at the `/bitnami/mongodb` path of the container.

The chart mounts a [Persistent Volume](https://kubernetes.io/docs/concepts/storage/persistent-volumes/) at this location. The volume is created using dynamic volume provisioning.

### Adjust permissions of persistent volume mountpoint

As the image run as non-root by default, it is necessary to adjust the ownership of the persistent volume so that the container can write data into it.

By default, the chart is configured to use Kubernetes Security Context to automatically change the ownership of the volume. However, this feature does not work in all Kubernetes distributions.
As an alternative, this chart supports using an initContainer to change the ownership of the volume before mounting it in the final destination.

You can enable this initContainer by setting `volumePermissions.enabled` to `true`.

### Adding extra volumes

The Bitnami Kibana chart supports mounting extra volumes (either PVCs, secrets or configmaps) by using the `extraVolumes` and `extraVolumeMounts` properties (available in the `mongos`, `shardsvr.dataNode`, `shardsvr.arbiter`, `configsvr` and `common` sections). This can be combined with advanced operations like adding extra init containers and sidecars.

### Setting Pod's affinity

This chart allows you to set your custom affinity using the `XXX.affinity` parameter(s). Find more information about Pod's affinity in the [kubernetes documentation](https://kubernetes.io/docs/concepts/configuration/assign-pod-node/#affinity-and-anti-affinity).

As an alternative, you can use of the preset configurations for pod affinity, pod anti-affinity, and node affinity available at the [bitnami/common](https://github.com/bitnami/charts/tree/main/bitnami/common#affinities) chart. To do so, set the `XXX.podAffinityPreset`, `XXX.podAntiAffinityPreset`, or `XXX.nodeAffinityPreset` parameters.

## Troubleshooting

Find more information about how to deal with common errors related to Bitnami's Helm charts in [this troubleshooting guide](https://docs.bitnami.com/general/how-to/troubleshoot-helm-chart-issues).

## Upgrading

If authentication is enabled, it's necessary to set the `auth.rootPassword` and `auth.replicaSetKey` when upgrading for readiness/liveness probes to work properly. When you install this chart for the first time, some notes will be displayed providing the credentials you must use. Please note down the password, and run the command below to upgrade your chart:

```console
helm upgrade my-release oci://REGISTRY_NAME/REPOSITORY_NAME/mongodb-sharded --set auth.rootPassword=[PASSWORD] (--set auth.replicaSetKey=[auth.replicaSetKey])
```

> Note: You need to substitute the placeholders `REGISTRY_NAME` and `REPOSITORY_NAME` with a reference to your Helm chart registry and repository. For example, in the case of Bitnami, you need to use `REGISTRY_NAME=registry-1.docker.io` and `REPOSITORY_NAME=bitnamicharts`.
> Note: you need to substitute the placeholders [PASSWORD] and [auth.replicaSetKey] with the values obtained in the installation notes.

### To 7.0.0

This major version updates the MongoDB&reg; container image version used from 6.0 to 7.0, the new stable version. There are no major changes in the chart, but we recommend checking the [MongoDB&reg; 7.0 release notes](https://www.mongodb.com/docs/manual/release-notes/7.0/) before upgrading.

> Note: Due to an error in our release process, the latest version in the previous major branch (6.6.8) already uses 7.0 by default, see [PR#19575](https://github.com/bitnami/charts/pull/19575)

### To 5.0.0

This major release renames several values in this chart and adds missing features, in order to be inline with the rest of assets in the Bitnami charts repository.

Affected values:

- Authentication parameters are reorganized under the `auth.*` parameter:
  - `usePassword` is renamed to `auth.enabled`.
  - `mongodbRootPassword`, `replicaSetKey`, `existingSecret` and `usePasswordFile` are now `auth.rootPassword`, `auth.replicaSetKey`, `auth.existingSecret` and `auth.usePasswordFile` respectively.
- `common.containerPorts.mongo` is renamed to `common.containerPorts.mongodb`
- `pdb.enabled` is renamed to `pdb.create`
- `XXX.replicas` is renamed to `XXX.replicaCount`
- `service.port` is renamed to `service.ports.mongodb`
- `metrics.containerPort` is renamed to `metrics.containerPorts.metrics`
- `service.nodePort` is renamed to `service.nodePorts.mongodb`
- `securityContext` is splitted into `podSecurityContext` and `containerSecurityContext` and moved into the different sections (`mongos`, `shardsvr.dataNode`, `shardsvr.arbiter`and `configsvr`):
  - `securityContext.fsGroup` is renamed to `XXX.podSecurityContext.fsGroup`
  - `securityContext.runAsUser` is renamed to `XXX.containerSecurityContext.runAsUser`
  - `securityContext.runAsNonRoot` is renamed to `XXX.containerSecurityContext.runAsNonRoot`
- `redinessProbe`, `livenessProbe` and `startupProbe` are moved to the different sections (`mongos`, `shardsvr.dataNode`, `shardsvr.arbiter`and `configsvr`)

### To 4.0.0

In this version, the mongodb-exporter bundled as part of this Helm chart was updated to a new version which, even it is not a major change, can contain breaking changes (from `0.11.X` to `0.30.X`).
Please visit the release notes from the upstream project at <https://github.com/percona/mongodb_exporter/releases>

### To 3.1.0

This version introduces `bitnami/common`, a [library chart](https://helm.sh/docs/topics/library_charts/#helm) as a dependency. More documentation about this new utility could be found [here](https://github.com/bitnami/charts/tree/main/bitnami/common#bitnami-common-library-chart). Please, make sure that you have updated the chart dependencies before executing any upgrade.

### To 3.0.0

[On November 13, 2020, Helm v2 support was formally finished](https://github.com/helm/charts#status-of-the-project), this major version is the result of the required changes applied to the Helm Chart to be able to incorporate the different features added in Helm v3 and to be consistent with the Helm project itself regarding the Helm v2 EOL.

#### What changes were introduced in this major version?

- Previous versions of this Helm Chart use `apiVersion: v1` (installable by both Helm 2 and 3), this Helm Chart was updated to `apiVersion: v2` (installable by Helm 3 only). [Here](https://helm.sh/docs/topics/charts/#the-apiversion-field) you can find more information about the `apiVersion` field.
- The different fields present in the *Chart.yaml* file has been ordered alphabetically in a homogeneous way for all the Bitnami Helm Charts

#### Considerations when upgrading to this version

- If you want to upgrade to this version from a previous one installed with Helm v3, you shouldn't face any issues
- If you want to upgrade to this version using Helm v2, this scenario is not supported as this version doesn't support Helm v2 anymore
- If you installed the previous version with Helm v2 and wants to upgrade to this version with Helm v3, please refer to the [official Helm documentation](https://helm.sh/docs/topics/v2_v3_migration/#migration-use-cases) about migrating from Helm v2 to v3

#### Useful links

- <https://docs.bitnami.com/tutorials/resolve-helm2-helm3-post-migration-issues/>
- <https://helm.sh/docs/topics/v2_v3_migration/>
- <https://helm.sh/blog/migrate-from-helm-v2-to-helm-v3/>

### To 2.0.0

MongoDB&reg; container images were updated to `4.4.x` and it can affect compatibility with older versions of MongoDB&reg;. Refer to the following guide to upgrade your applications:

- [Upgrade a Sharded Cluster to 4.4](https://docs.mongodb.com/manual/release-notes/4.4-upgrade-sharded-cluster/)

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