# Troubleshooting Prometheus Grafana Setup

This guide provides troubleshooting steps for common errors encountered during the setup of Prometheus and Grafana in a Kubernetes cluster.
Pod Scheduling Errors

## Not getting appropriate metrics
### First I got only system related metrics like only for CPU and memory, but I need kube-state-metrics. So I followed one article.

Solution: 
    https://devopscube.com/setup-kube-state-metrics/


## Service Discovery Issues:
## Issue: Prometheus cannot discover targets

### If Prometheus cannot discover the targets it's supposed to monitor, it might be due to misconfigured service discovery settings or network issues.

Solution:

    Verified the Prometheus configuration for service discovery mechanisms such as Kubernetes service discovery.
    Added that in the prometheus.yaml ConfigMap file   
    
## Configuration Errors:
## Issue: Invalid YAML configuration (crash loop back)

### Errors in the YAML configuration files used to deploy Prometheus or Grafana can cause deployment failures.

Solution:

    Validated the YAML configuration files for syntax errors, indentation issues, and missing or incorrect field values.
    Used command like kubectl apply --dry-run=client -f <file.yaml> to check the validity of YAML files before applying them to the cluster.

## Issue: Missing ConfigMaps or Secrets

### If required configuration files or secrets are missing, Prometheus or Grafana pods might fail to start.  

Solution:

    Ensured that all necessary ConfigMaps and Secrets are created and properly mounted into the Prometheus and Grafana pods.
    Checked the existence and correctness of ConfigMaps and Secrets referenced in the pod specifications.

## Networking Issues:
## Issue: Connection timeout

### If there are network connectivity issues between Prometheus, Grafana, and other components in the cluster, you might encounter connection timeouts or errors.

Solution:

    Verified network connectivity between Prometheus, Grafana, and their respective targets using command like ping, or curl.
    Check for network policies or firewall rules blocking communication between the components.
    
## Persistent Storage Problems:
## Issue: VolumeMount errors

### If there are issues with mounting persistent volumes for Prometheus or Grafana data storage, pods might fail to start.

Solution:

    Checked the PersistentVolume (PV) and PersistentVolumeClaim (PVC) configurations to ensure they match and are correctly provisioned.

## Container Image Pull Failures:
## Issue: ImagePullBackOff

### If Kubernetes is unable to pull the container images for Prometheus or Grafana, pods might fail to start due to image pull failures.

Solution:

    Checked the availability of the container images in the specified container registry.
    
