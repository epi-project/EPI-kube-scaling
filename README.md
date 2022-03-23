# EPI-kube-scaling
In this repository we add scaling techniques to the EPI framework setup to demonstrate scaling capabilities under stress test experiments.

## Deploying secvices; here we assume you have a kubernetes master and worker nodes running and configured
```shell
  $ cd EPI-services
  $ kubectl apply -f decrypt.yaml #BF1 = The decryption server
  $ kubectl apply -f encrypt.yaml #BF2 = The encryption server
  $ kubectl apply -f firewall.yaml #BF3 = The firewall server
  $ kubectl apply -f proxy.yaml #The SOCKS proxy
  $ kubectl apply -f socat.yaml #The end server
```
## Start the client script, refer to the poc repository 

```shell
  $ docker-compose up -d
  $ pipenv install click socksx
  $ pipenv shell
  $ cd Scripts
  $ locust -f ./locust.py --headless -u <number of clients> -r <spawn rate> -H <destination IP>
```

## In HPA and VPA path there's example deployment of scalers/ service.
##Deploy if needed.
  
## To collect matrices, you need to successfully deploy the metric server, after you can run the collecting script
```shell
  $ cd Scripts 
  $ ./getResourcesCSV.sh --help 
  $ ./getResourcesCSV.sh -n default --no-headers -o <filename>.csv
  ```
