### Goal
To ensure the incoming traffic get to their desired destination inside a cluster.

#### Ingress
Is a native object inside the cluster.
Route trafic from outside the cluster to one or more services inside the cluster.
Is designed to handle HTTP and HTTPS traffic.
Can route to multiple service.

#### Load Balancer
Is an extension of a service.
A cluster must be running on a provider that supports external load balancers.
Can only route to a single service.

Link: (https://www.baeldung.com/ops/kubernetes-ingress-vs-load-balancer)
