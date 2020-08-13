# EKS-with-Autoscale

## Getting Started setup EKS cluster on AWS

First of all setup EKS by writing cluster.yaml file and run it with following command

``` kubectl apply -f cluster.yaml ```

**OUTPUTS**

![Screenshot](./images/aws-eks-1.png)

![Screenshot](./images/eks-output2.png)

Next step is Setting metrics server in kubernetes for checking CPU and Memory usage using this link 

``` kubectl apply -f https://github.com/kubernetes-sigs/metrics-server/releases/download/v0.3.7/components.yaml ```


After that run Deployment and service Mainfest file which is exposed through Loadbalancer with port 3000. 

``` kubectl apply -f deployment.yaml ```

``` kubectl apply -f service.yaml ```

Then run HPA (Horizontal Pod Autoscaler) file for CPU and Memory Mainfest file and the thresold will be 50% CPU and 60% Memory.
 
``` kubectl apply -f hpa-cpu.yaml ```

``` kubectl apply -f hpa-memory.yaml ```

**OUTPUTS FOR CPU AND MEMORY UTILIZATION**

![Screenshot](./images/top.png)


## Load testing using siege and Jmeter Tool.

1. For siege use this command:- ``` siege -q -c 250 -t 1m  http://mywebsite.com ```

