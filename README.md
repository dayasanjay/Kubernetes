### Kubernetes

<b> What is kubernetes?</b><br>

Kubernetes is a portable, extensible, open-source platform for managing containerized workloads and services, that facilitates both declarative configuration and automation. It has a large, rapidly growing ecosystem. Kubernetes services, support, and tools are widely available.<br>

The name Kubernetes originates from Greek, meaning helmsman or pilot. K8s as an abbreviation results from counting the eight letters between the "K" and the "s". Google open-sourced the Kubernetes project in 2014. Kubernetes combines over 15 years of Google's experience running production workloads at scale with best-of-breed ideas and practices from the community.<br>


### Why you need Kubernetes and what it can do?

Containers are a good way to bundle and run your applications. In a production environment, you need to manage the containers that run the applications and ensure that there is no downtime. For example, if a container goes down, another container needs to start.<br>

That's how Kubernetes comes to the rescue! Kubernetes provides you with a framework to run distributed systems resiliently. It takes care of scaling and failover for your application, provides deployment patterns, and more. For example, Kubernetes can easily manage a canary deployment for your system.<br>

### What Kubernetes can provide?

<b>Service discovery and load balancing</b> : Kubernetes can expose a container using the DNS name or using their own IP address. If traffic to a container is high, Kubernetes is able to load balance and distribute the network traffic so that the deployment is stable.<br>
  
<b>Storage orchestration</b> : Kubernetes allows you to automatically mount a storage system of your choice, such as local storages, public cloud providers, and more.<br>
  
<b>Automated rollouts and rollbacks</b> : You can describe the desired state for your deployed containers using Kubernetes, and it can change the actual state to the desired state at a controlled rate. For example, you can automate Kubernetes to create new containers for your deployment, remove existing containers and adopt all their resources to the new container.<br>

<b>Automatic bin packing</b> : You provide Kubernetes with a cluster of nodes that it can use to run containerized tasks. You tell Kubernetes how much CPU and memory (RAM) each container needs. Kubernetes can fit containers onto your nodes to make the best use of your resources.<br>
  
<b>Self-healing</b> : Kubernetes restarts containers that fail, replaces containers, kills containers that don't respond to your user-defined health check, and doesn't advertise them to clients until they are ready to serve.<br>
  
<b>Secret and configuration management</b> : Kubernetes lets you store and manage sensitive information, such as passwords, OAuth tokens, and SSH keys. You can deploy and update secrets and application configuration without rebuilding your container images, and without exposing secrets in your stack configuration.<br>
### Kubernetes Components
When we deploy Kubernetes, you get a cluster.<br>

A Kubernetes cluster consists of a set of worker machines, called nodes, that run containerized applications. Every cluster has at least one worker node.<br>

The worker node(s) host the Pods that are the components of the application workload. The control plane manages the worker nodes and the Pods in the cluster. In production environments, the control plane usually runs across multiple computers and a cluster usually runs multiple nodes, providing fault-tolerance and high availability.<br>

This document outlines the various components you need to have for a complete and working Kubernetes cluster.<br>
### Control Plane Components
The control plane's components make global decisions about the cluster (for example, scheduling), as well as detecting and responding to cluster events (for example, starting up a new pod when a deployment's replicas field is unsatisfied).<br>

Control plane components can be run on any machine in the cluster. However, for simplicity, set up scripts typically start all control plane components on the same machine, and do not run user containers on this machine. See Creating Highly Available clusters with kubeadm for an example control plane setup that runs across multiple machines.<br>

<b>kube-apiserver </b>

The API server is a component of the Kubernetes control plane that exposes the Kubernetes API. The API server is the front end for the Kubernetes control plane.<br>

The main implementation of a Kubernetes API server is kube-apiserver. kube-apiserver is designed to scale horizontally—that is, it scales by deploying more instances. You can run several instances of kube-apiserver and balance traffic between those instances.<br>
<b>etcd</b>

Consistent and highly-available key value store used as Kubernetes' backing store for all cluster data.<br>

If your Kubernetes cluster uses etcd as its backing store, make sure you have a back up plan for those data.<br>

You can find in-depth information about etcd in the official documentation.<br>

<b>kube-scheduler</b>

Control plane component that watches for newly created Pods with no assigned node, and selects a node for them to run on.<br>

Factors taken into account for scheduling decisions include: individual and collective resource requirements, hardware/software/policy constraints, affinity and anti-affinity specifications, data locality, inter-workload interference, and deadlines.<br>

<b>kube-controller-manager</b>

Control plane component that runs controller processes.<br>

Logically, each controller is a separate process, but to reduce complexity, they are all compiled into a single binary and run in a single process.<br>

<b>Some types of these controllers are:</b>

1. Node controller: Responsible for noticing and responding when nodes go down.<br>
2. Job controller: Watches for Job objects that represent one-off tasks, then creates Pods to run those tasks to completion.<br>
3. Endpoints controller: Populates the Endpoints object (that is, joins Services & Pods).<br>
4. Service Account & Token controllers: Create default accounts and API access tokens for new namespaces.<br> 
















































