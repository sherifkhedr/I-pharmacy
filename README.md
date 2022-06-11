# I-pharmacy Infrastructure

# syllabus

* Discribtion
* Kubernetes architecture
* How to deploy
* How to upgrade

Infrastructure is deployed in kubbernetes consist from  3 server 
1. kubernetes
2. reverse proxy
3. nfs

## kubernetes architecture  

![k8s](https://github.com/sherifkhedr/I-pharmacy/blob/master/infrak8s.drawio.png)   

| vm name | private ip  | public ip |  
|--------|--------|---------------------|
| master |  10.114.0.3  | 207.154.226.237 |
| worker01 |       10.114.0.4 |  207.154.238.25 |
| reverse proxy + nfs |  10.114.0.5    |      138.68.74.211      | 
| pod network cidr| 10.244.0.0/16 |

### name spaces :  
      admin-app   : containin admin application (pod) 
      backend-api : contain backend api application (pod)  
      database    : contain sql server database version 17
      kube-system : contain k8s pod itself
      nfs-storage : for nfs provision storage
      traefik     : for ingress controller
      portal      : contain portal appplication

### nodes:
* Master : manage kuberneets cluster and contain system component
* Worker01 : for deploying applications (pod) on it 
* Reverse proxy + nfs : contain haproyx as reverse proxy to forward traffic from outside into k8s cluster
it's configuration resides in ```/etc/haproxy/haproxy.cfg```
if you wat to add mode nodes you can do it through backend sections

* Nfs Storage : on the same reverse proxy server the data located in /srv/kubernetes/
you can display exposed folder by running command :
``` exportfs -v or showmount -e ```

### ingress:
   * traefik : to redirect traffic from reverse cluster to the application in a pod 
    each application deployed in k8s cluster have ingress rule and also (admin + portal + api ) have ingress rule
    ingress rule is namespaced for example if you want to get ingress rule for admin by running this command :
        ``` kubectl get ingress ```

### How to deploy application in k8s
the applications are deployed by Helm Charts so you can edit values.yaml to change the tag of the image to new one and run this command:
```helm upgrade (Release name) -n (name space) ```