# k8s-resources

# Volumes:
----------
EBS
====

Static Provisioning
--------------------
1. We need to create volumes maually
2. We need to install the drivers. 
        kubectl apply -k "github.com/kubernetes-sigs/aws-ebs-csi-driver/deploy/kubernetes/overlays/stable/?ref=release-1.52"
3. EKS nodes should have permissions to access EBS volumes

4. change Volume-id in yaml file and change zone-id where you created regional volume 
5. If we want access from Internet we need to allow our sevice port in security-group


dynamic provisioning
-------------------------------
1. install drivers
2. give permissions ec2 nodes

storageClass
-----------------
admin creates one storage class for EBS for expense project.

EFS
====

Static Provisioning:
--------------------
1. create EFS volume
2. install drivers and allow 2049 traffic from EKS worker nodes
    2.1  kubectl kustomize \
         "github.com/kubernetes-sigs/aws-efs-csi-driver/deploy/kubernetes/overlays/stable/?ref=release-2.1" > public-ecr-driver.yaml
    2.2  kubectl apply -f public-ecr-driver.yaml
3. give permision to EKS nodes
4. create PV
5. create PVC
6. claim through pod using PVC
7. open node port in EKS worker nodes

dynamic provisioning
-------------------------------
1. install drivers
2. give permissions ec2 nodes

storageClass
-----------------
admin creates one storage class for EFS for expense project.
note: access points will create for each application individually in efs , this is dynamic but not EFS volume.
