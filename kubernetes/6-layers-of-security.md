## The 6 layers of Kubernetes security

1. Authentication
2. RBAC
3. Pod Security
4. Image Scanning
5. Network Policies
6. Cluster Hygiene

(https://itnext.io/kubernetes-security-for-beginners-a-2025-survival-guide-9f162fe5dee0)

### 1. Authentication
Lock the Gates
#### Step 1. Disable Anonymous Access
```
kubectl delete clusterrolebinding system:anonymous
```

#### Step 2. Use Cloud Provider IAM
**EKS**: Integrate with IAM roles.
```
kubectl get pods --as=system:anonymous
```

### 2. RBAC
Keys to the Kingdom
1. Role and RoleBinding
2. ServiceAccount

### 3. Pod Security
Block risky containers
1. Enforce Pod Security Admission (PSA)
2. Kyverno for Custom Policies

### 4. Image Scanning
Stop Vulnerabilities
1. Trivy
2. Block Vulnerables Images in CI/CD

### 5. Network Policies
Isolate Pods

### 6. Cluster Hygiene
Fix CIS Misconfigurations
