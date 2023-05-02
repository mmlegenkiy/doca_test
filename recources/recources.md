# Working with Pods
You'll rarely create individual Pods directly in Kubernetes—even singleton Pods. This is because Pods are designed as relatively ephemeral, disposable entities. When a Pod gets created (directly by you, or indirectly by a [controller](https://kubernetes.io/docs/concepts/architecture/controller/)), the new Pod is scheduled to run on a Node in your cluster. The Pod remains on that node until the Pod finishes execution, the Pod object is deleted, the Pod is evicted for lack of resources, or the node fails.

> Restarting a container in a Pod should not be confused with restarting a Pod. A Pod is not a process, but an environment for running container(s). A Pod persists until it is deleted.

## Pod OS
You should set the `.spec.os.name` field to either windows or linux to indicate the OS on which you want the pod to run. These two are the only operating systems supported for now by Kubernetes. In future, this list may be expanded.

In Kubernetes v1.27, the value you set for this field has no effect on scheduling of the pods. Setting the .spec.os.name helps to identify the pod OS authoratitively and is used for validation. The kubelet refuses to run a Pod where you have specified a Pod OS, if this isn't the same as the operating system for the node where that kubelet is running. The Pod security standards also use this field to avoid enforcing policies that aren't relevant to that operating system.

## Pods and controllers
You can use workload resources to create and manage multiple Pods for you. A controller for the resource handles replication and rollout and automatic healing in case of Pod failure. For example, if a Node fails, a controller notices that Pods on that Node have stopped working and creates a replacement Pod. The scheduler places the replacement Pod onto a healthy Node. 
