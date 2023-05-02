# Using Pods

The following is an example of a Pod which consists of a container running the image `nginx:1.14.2`.
```yaml
apiVersion: v1
kind: Pod
metadata:
  name: nginx
spec:
  containers:
  - name: nginx
    image: nginx:1.14.2
    ports:
    - containerPort: 80
```
To create the Pod shown above, run the following command:

`kubectl apply -f https://k8s.io/examples/pods/simple-pod.yaml`

Pods are generally not created directly and are created using workload resources. See [Working with Pods](https://kubernetes.io/docs/concepts/workloads/pods/#working-with-pods "Reference") for more information on how Pods are used with workload resources.

