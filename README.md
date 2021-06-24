k8s-wordpress-service
=========

A pack kubernetes objects required to apply wordpress on your kubernetes cluster.

Requirements
------------

- Kubernetes cluster
- 4GB free space on disk for 2 PersistentVolume's 
- Created directories on node where objectes will be applied:
```
mkdir -p /tmp/data/lv-1  
mkdir -p /tmp/data/lv-2
```

Variables
--------------
In wordpress-deployment.yaml 
```
spec:
  externalIPs:
  - <your_ip_address>
  ports:
    - port: <your_port_number>
```

Encrypt your password and username:
```
echo -n 'my-pass' | base64
```
In secrets.yaml  set password (default is "changeme123") and you can leave db-user (default is "root")
```
  pass: <put_here__encrypted_password_for_DB>
  
```

Fast Test
--------
1. Create 2 directories for PersistentVolume's 
2. Change ip address for your own
3. Set encrypted username (default is "root") and password for DB (default is "changeme123")
4. Paste it on node where you have access to API
```
git clone https://github.com/Sarvatus/k8s-wordpress-service.git  
kubectl apply -f k8s-wordpress-service
```