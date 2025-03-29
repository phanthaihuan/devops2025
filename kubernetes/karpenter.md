#### What
1. AWS's open-source node autoscaler for Kubernetes.
2. Is a Kubernetes-native autoscaler.
3. Is a CNCF project under SIG Autoscaling.
4. Provisions the right nodes at the right time.
5. Directly provisions EC2 instances based on the workload requirements

#### How
1. Direct EC2 provisioning.
2. Workload-driven scaling.
3. Automatic instance selection.
4. Kubernetes-native.
5. Consolidation and right-sizing.

#### Two Primary Custom Resources:
1. NodePool: what kind of nodes Karpenter will create.
2. EC2NodeClass: specifies AWS-specific configuration for the nodes.

#### Key Metrics for monitoring to track:
1. karpenter_nodes_created
2. karpenter_nodes_terminated
3. karpenter_pods_pending
4. karpenter_provisioner_scheduling_duration_seconds

#### Links
https://blog.diatomlabs.com/mastering-eks-scaling-with-karpenter-a-practical-guide-a6e239645a45
