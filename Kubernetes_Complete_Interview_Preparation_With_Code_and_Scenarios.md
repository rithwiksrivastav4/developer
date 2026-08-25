# Kubernetes Complete Interview Preparation Guide (2 Years Experience)

# Table of Contents

1.  Kubernetes Introduction
2.  Kubernetes Architecture
3.  Kubernetes Components
4.  Kubernetes Objects
5.  YAML Basics
6.  Pods
7.  ReplicaSet
8.  Deployments
9.  Services
10. Namespaces
11. ConfigMaps
12. Secrets
13. Volumes
14. Persistent Volumes
15. Networking
16. Health Checks
17. Resource Management
18. Scaling
19. Rolling Updates
20. Rollbacks
21. Helm
22. Kubernetes with Docker
23. Kubernetes CI/CD
24. Production Scenarios
25. Interview Questions
26. kubectl Command Cheat Sheet

# 1. What is Kubernetes?

Kubernetes is a container orchestration platform used to deploy, manage,
scale, and maintain containerized applications.

## Problems Kubernetes Solves

Without Kubernetes:

    Developer
     |
    Docker Container
     |
    Manual Deployment
     |
    Manual Scaling

With Kubernetes:

    Developer

     |

    Docker Image

     |

    Kubernetes Cluster

     |

    Automatic Deployment

     |

    Scaling + Recovery + Load Balancing

## Kubernetes Features

-   Automatic deployment
-   Self healing
-   Auto scaling
-   Load balancing
-   Service discovery
-   Rolling updates
-   Secret management

------------------------------------------------------------------------

# 2. Kubernetes Architecture

                     Kubernetes Cluster

                          |
            --------------------------------

            Control Plane              Worker Node

            API Server                 Kubelet
            Scheduler                  Kube Proxy
            Controller Manager         Container Runtime
            etcd                       Pods

# 3. Control Plane Components

## API Server

API Server is the entry point of Kubernetes.

Example:

``` bash
kubectl get pods
```

Flow:

    kubectl

     |

    API Server

     |

    etcd

Responsibilities:

-   Authentication
-   Validation
-   Communication

------------------------------------------------------------------------

## etcd

etcd is a distributed key-value database.

Stores:

-   Cluster state
-   Pod information
-   Configuration
-   Secrets

Example:

    Pod Name
    Node Details
    Service Information

------------------------------------------------------------------------

## Scheduler

Scheduler decides where pods should run.

Example:

    New Pod

     |

    Scheduler

     |

    Select Worker Node

     |

    Create Pod

Checks:

-   CPU
-   Memory
-   Node labels
-   Availability

------------------------------------------------------------------------

## Controller Manager

Maintains desired state.

Example:

Desired:

    replicas: 3

Current:

    2 Pods

Controller creates:

    1 New Pod

------------------------------------------------------------------------

# 4. Worker Node Components

## Kubelet

Agent running on every worker node.

Responsibilities:

-   Creates containers
-   Reports pod status
-   Communicates with API server

------------------------------------------------------------------------

## Container Runtime

Runs containers.

Examples:

-   containerd
-   CRI-O

------------------------------------------------------------------------

## Kube Proxy

Handles:

-   Network routing
-   Service communication

------------------------------------------------------------------------

# 5. Kubernetes YAML Basics

Most Kubernetes objects are created using YAML files.

Example:

``` yaml
apiVersion: v1

kind: Pod

metadata:
  name: nginx-pod

spec:
  containers:
  - name: nginx
    image: nginx
```

Apply YAML:

``` bash
kubectl apply -f pod.yaml
```

Delete:

``` bash
kubectl delete -f pod.yaml
```

------------------------------------------------------------------------

# 6. Pods

Pod is the smallest Kubernetes deployable unit.

Example:

    Pod

     |
     |--- Application Container
     |
     |--- Sidecar Container

## Pod YAML Example

``` yaml
apiVersion: v1

kind: Pod

metadata:
  name: node-app

spec:

  containers:

  - name: backend

    image: node:18

    ports:

    - containerPort: 5000
```

Commands:

``` bash
kubectl get pods

kubectl describe pod node-app

kubectl logs node-app

kubectl delete pod node-app
```

------------------------------------------------------------------------

# 7. ReplicaSet

ReplicaSet maintains the required number of pods.

Example:

``` yaml
apiVersion: apps/v1

kind: ReplicaSet

metadata:

 name: nginx-rs


spec:

 replicas: 3

 selector:

  matchLabels:

   app: nginx


 template:

  metadata:

   labels:

    app: nginx


  spec:

   containers:

   - name: nginx

     image: nginx
```

------------------------------------------------------------------------

# 8. Deployment

Deployment manages:

-   ReplicaSets
-   Rolling updates
-   Rollbacks

Example:

``` yaml
apiVersion: apps/v1

kind: Deployment


metadata:

 name: node-app


spec:

 replicas: 3


 selector:

  matchLabels:

   app: node


 template:

  metadata:

   labels:

    app: node


  spec:

   containers:

   - name: api

     image: my-node-app:v1

     ports:

     - containerPort:5000
```

Create:

``` bash
kubectl apply -f deployment.yaml
```

Check:

``` bash
kubectl get deployments
```

------------------------------------------------------------------------

# 9. Kubernetes Service

Service exposes pods.

Types:

1.  ClusterIP
2.  NodePort
3.  LoadBalancer

## ClusterIP Example

``` yaml
apiVersion: v1

kind: Service

metadata:

 name: backend-service


spec:

 selector:

  app: backend


 ports:

 - port:5000

   targetPort:5000
```

------------------------------------------------------------------------

## NodePort Example

``` yaml
apiVersion: v1

kind: Service


metadata:

 name: frontend


spec:

 type: NodePort


 ports:

 - port:80

   nodePort:30080
```

------------------------------------------------------------------------

## LoadBalancer

Used in cloud environments.

Example:

AWS:

    Internet

     |

    AWS Load Balancer

     |

    Kubernetes Service

     |

    Pods

------------------------------------------------------------------------

# 10. Namespace

Namespaces separate resources.

Example:

    Cluster

     |
     |--- Development

     |
     |--- Testing

     |
     |--- Production

Commands:

``` bash
kubectl get namespaces

kubectl create namespace dev
```

------------------------------------------------------------------------

# 11. ConfigMap

Stores application configuration.

Example:

``` yaml
apiVersion: v1

kind: ConfigMap


metadata:

 name: app-config


data:

 DATABASE_URL: mysql://db
```

Use cases:

-   Environment variables
-   Configuration files

------------------------------------------------------------------------

# 12. Secrets

Stores sensitive information.

Example:

``` yaml
apiVersion: v1

kind: Secret


metadata:

 name: database-secret


data:

 password: cGFzc3dvcmQ=
```

Used for:

-   Passwords
-   Tokens
-   API keys

------------------------------------------------------------------------

# 13. Volumes

Containers are temporary.

Volumes provide persistent storage.

Types:

-   emptyDir
-   Persistent Volume
-   Persistent Volume Claim

------------------------------------------------------------------------

# 14. Persistent Volume Example

Persistent Volume:

``` yaml
apiVersion: v1

kind: PersistentVolume


metadata:

 name: pv-storage


spec:

 capacity:

  storage: 5Gi

 accessModes:

 - ReadWriteOnce
```

------------------------------------------------------------------------

# 15. Health Checks

## Liveness Probe

Checks if application is alive.

Example:

``` yaml
livenessProbe:

 httpGet:

  path: /

  port: 8080
```

## Readiness Probe

Checks if application is ready.

``` yaml
readinessProbe:

 httpGet:

  path: /health

  port: 8080
```

------------------------------------------------------------------------

# 16. Resource Management

Example:

``` yaml
resources:

 requests:

  memory: "256Mi"

  cpu: "250m"


 limits:

  memory: "512Mi"

  cpu: "500m"
```

------------------------------------------------------------------------

# 17. Scaling

## Manual Scaling

``` bash
kubectl scale deployment app --replicas=5
```

## Horizontal Pod Autoscaler

Example:

    CPU increases

     |

    HPA detects

     |

    Creates new pods

Command:

``` bash
kubectl autoscale deployment app --cpu-percent=70 --min=2 --max=10
```

------------------------------------------------------------------------

# 18. Rolling Updates

Update image:

``` bash
kubectl set image deployment/app app=image:v2
```

Check:

``` bash
kubectl rollout status deployment/app
```

------------------------------------------------------------------------

# 19. Rollback

Rollback deployment:

``` bash
kubectl rollout undo deployment/app
```

------------------------------------------------------------------------

# 20. Helm

Helm is Kubernetes package manager.

Commands:

Install:

``` bash
helm install myapp chart-name
```

Upgrade:

``` bash
helm upgrade myapp chart-name
```

Remove:

``` bash
helm uninstall myapp
```

------------------------------------------------------------------------

# 21. Kubernetes with Docker

Flow:

    Developer

     |

    Dockerfile

     |

    Docker Image

     |

    Docker Registry

     |

    Kubernetes Deployment

     |

    Pods

     |

    Containers

------------------------------------------------------------------------

# 22. Kubernetes CI/CD Pipeline

    Developer

     |

    GitHub

     |

    GitHub Actions

     |

    Docker Build

     |

    Push Image

     |

    Kubernetes Deploy

     |

    Application Live

------------------------------------------------------------------------

# 23. kubectl Commands

## Cluster

``` bash
kubectl cluster-info

kubectl get nodes
```

## Pods

``` bash
kubectl get pods

kubectl logs pod-name

kubectl exec -it pod-name -- bash
```

## Services

``` bash
kubectl get svc
```

## Deployments

``` bash
kubectl get deployments

kubectl describe deployment app
```

## Debug

``` bash
kubectl describe pod pod-name

kubectl logs pod-name

kubectl get events
```

------------------------------------------------------------------------

# Kubernetes Scenario Based Interview Questions

## Q1. Pod is not starting. How do you debug?

Answer:

Check:

``` bash
kubectl get pods

kubectl describe pod pod-name

kubectl logs pod-name
```

Possible issues:

-   Wrong image
-   Application crash
-   Missing configuration
-   Resource problem

------------------------------------------------------------------------

# Q2. Pod is continuously restarting. Why?

Possible reasons:

-   Application failure
-   Database connection issue
-   Wrong environment variables
-   Memory limit exceeded

Debug:

``` bash
kubectl logs pod-name

kubectl describe pod pod-name
```

------------------------------------------------------------------------

# Q3. Application is running but not accessible?

Check:

``` bash
kubectl get pods

kubectl get service

kubectl get endpoints
```

Verify:

-   Service selector
-   Port mapping
-   Network policy

------------------------------------------------------------------------

# Q4. How does Kubernetes self-healing work?

Answer:

Kubernetes controllers monitor desired state.

Example:

    Pod crashes

     |

    Controller detects

     |

    New Pod created

------------------------------------------------------------------------

# Q5. Difference between Pod and Container?

Container:

-   Runs application

Pod:

-   Kubernetes wrapper containing containers

------------------------------------------------------------------------

# Q6. Deployment vs StatefulSet?

Deployment:

-   Stateless applications

Example:

-   Web servers

StatefulSet:

-   Stateful applications

Example:

-   Databases

------------------------------------------------------------------------

# Q7. ConfigMap vs Secret?

ConfigMap:

-   Normal configuration

Secret:

-   Sensitive data

------------------------------------------------------------------------

# Q8. Node failure scenario?

Kubernetes:

1.  Detects failed node
2.  Removes unhealthy pods
3.  Creates pods on available nodes

------------------------------------------------------------------------

# Q9. High CPU usage in production?

Commands:

``` bash
kubectl top pods

kubectl top nodes
```

Solutions:

-   Increase resources
-   Enable HPA
-   Optimize application

------------------------------------------------------------------------

# Q10. How does kubectl apply work internally?

Flow:

    kubectl

     |

    API Server

     |

    etcd

     |

    Scheduler

     |

    Kubelet

     |

    Container

------------------------------------------------------------------------

# Production Best Practices

-   Use namespaces
-   Configure resource limits
-   Enable monitoring
-   Use health checks
-   Secure secrets
-   Use RBAC
-   Enable backups
-   Use rolling deployments

------------------------------------------------------------------------

# Kubernetes Interview Preparation Checklist

For 2 years experience:

-   Kubernetes architecture
-   Pods
-   Deployments
-   Services
-   ConfigMaps
-   Secrets
-   Volumes
-   Networking
-   Scaling
-   Rolling updates
-   Rollbacks
-   Helm
-   Docker integration
-   CI/CD deployment
-   Production debugging
-   Monitoring basics
