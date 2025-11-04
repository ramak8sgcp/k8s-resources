# k8s-resources

# Volumes:
----------

Static Provisioning
--------------------
EBS

1. We need to create volumes
2. We need to install the drivers.
3. EKS nodes should have permissions to access EBS volumes

4. change Volume-id in yaml file and change zone-id where you created regional volume 
5. If we want access from Internet we need to allow our sevice port in security-group