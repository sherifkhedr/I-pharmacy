# I-pharmacy Infrastructure
#syllabus

* Discribtion
* Kubernetes architecture
* How to deploy
* How to upgrade
 
Infrastructure is deployed in kubbernetes consist from  3 server 
1. kubernetes
2. reverse proxy
3. nfs

* kubernetes 

![k8s](https://github.com/sherifkhedr/I-pharmacy/blob/master/infrak8s.drawio.png)   

| vm name | private ip  | public ip |  
|--------|--------|---------------------|
| master |  10.114.0.3  | 207.154.226.237 |
| worker |       10.114.0.4 |  207.154.238.25 |
| reverse proxy + nfs |  10.114.0.5    |      138.68.74.211      | 
| pod network cidr| 10.244.0.0/16 |

* architecture : 
  1. namespaces: 
      admin-app   : containin admin application (pod) 
      backend-api : contain backend api application (pod)  
      database    : contain sql server database version 17
      kube-system : contain k8s pod itself
      nfs-storage : for nfs provision storage
      traefik     : for ingress controller
      portal      : contain portal appplication
