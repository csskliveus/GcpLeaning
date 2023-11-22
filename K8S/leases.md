Leases

Leases provide a mechanism to lock shared resources and co-ordinate activity between members of a set.

Lease concept is represented by Lease object in kubernetes in "coordination.k8s.io" API group.


Node heartbeats

Kubernetes uses the lease API to communicate kubelet node heartbeats to kubernetes API server.

For every node, there is a matching Lease object in kube-node-lease.
 
   Under the hood, every kubelet heartbeat is an update request to this "Lease" object, updating the spec.renewTime field for the Lease. 


Leader election

Kubernetes also uses Leases to ensure only one instance of a component is running at any given time.

This is used by control plane components like kube-controller-manager and kube-scheduler in HA configurations, where only one instance of the component should be actively running while the other instances are on stand-by.


