# How Pods manage multiple containers
Pods are designed to support multiple cooperating processes (as containers) that form a cohesive unit of service. The containers in a Pod are automatically co-located and co-scheduled on the same physical or virtual machine in the cluster. The containers can share resources and dependencies, communicate with one another, and coordinate when and how they are terminated.

For example, you might have a container that acts as a web server for files in a shared volume, and a separate "sidecar" container that updates those files from a remote source, as in the following diagram:
![Image](https://d33wubrfki0l68.cloudfront.net/aecab1f649bc640ebef1f05581bfcc91a48038c4/728d6/images/docs/pod.svg)

Some Pods have [init containers](https://kubernetes.io/docs/reference/glossary/?all=true#term-init-container) as well as [app containers](https://kubernetes.io/docs/reference/glossary/?all=true#term-app-container ':size=30%'). Init containers run and complete before the app containers are started.







