# I-pharmacy Infrastructure
## Describtion
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
| pod network cidr| 10.244.0.0/16       |