# 1- Hands-on lab Training webapp-iks-lab

Deploy a Scalable Web App on IKS cluster Workshop 

The purpose of this structured, no-cost, hands-on, instructor-led learning 
experience is to demonstrate how to combine different technologies such 
as Container Orchestration Platform, Container Registry, and cloud 
computing environment to kickstart cloud native applications. Specifically, 
the attendees will learn how to: 

Scaffold a starter web application, run it locally in a container, push the 
scaffolded code to a private Git repository

Deploy the application to a Red Hat OpenShift cluster on IBM Cloud

Monitor the health and performance of the application 

Auto-scale and manually scale the application
It is our goal that attendees will benefit from the workshop through the use of
Red Hat OpenShift on IBM Cloud to enable them to:

Build, deploy, manage, and sale applications faster and more cost-
effectively

Collaborate and accelerate their journey from proof of concept to 


## 2- Lab preparation
Follow these instructions for the setup of the initial Lab environment.

1- Create an access group in your IBM Cloud account: "Demo LABs"
https://cloud.ibm.com/iam/groups
Create
Enter "Demo LABs" as name of access group
Enter a short description
Add the following access polices:
	
1.1 VPC Infrastructure Services service
1.2 Cloud Object Storage service
1.3 Security Advisor service
1.4 All resource group
    resourceType string equals resource-group
1.5 Toolchain service
1.6 Certificate Manager service
1.7 Schematics service
1.8 All resources in account (including future IAM enabled services)

2- Create a resource group "labs"
https://cloud.ibm.com/account/resource-groups

3- Invite users to "Demo LABs" access group via:
https://cloud.ibm.com/iam/users/invite_users
enter user's email address
select "Demo LABs"

Users need to go to their notification section to accept the invite:
https://cloud.ibm.com/notifications
First time users of ibm cloud need to create a new ibm cloud id. Consult with your ibm contact for first time ID creation ( https://cloud.ibm.com/registration ) 

4- Work with your IKS team to deploy an IKS cluster required for this lab.

## 3- Objectives

Deploy a web application to the Kubernetes cluster.
Monitor the logs and health of the cluster.
Scale Kubernetes pods.


![plot](https://github.com/bkoohi/webapp-iks-lab/blob/main/images/Screen%20Shot%202022-04-01%20at%2011.49.40%20AM.png)

3.1- A developer downloads or clones a starter web application

3.2- Optionally build the application to produce a container image

3.3- Optionally the image is pushed to a namespace in the IBM Cloud Container Registry

3.4- The application is deployed to a Kubernetes cluster

3.5- Users access the application


## 4- Start a new IBM Cloud Shell
4.1 From the IBM Cloud console in your browser, select the account where you have been invited.

4.2 Click the button in the upper right corner to create a new Cloud Shell ( https://cloud.ibm.com/shell )


## 5- Clone a starter application

In this section, you will clone a GitHub repo with a simple Helm-based NodeJS starter application with a landing page and two endpoints to get started. You can always extend the starter application based on your requirement.

1- On a terminal, run the below command to clone the GitHub repository to your machine:

```
git clone https://github.com/IBM-Cloud/kubernetes-node-app
```
2- Change to the application directory,
```
cd kubernetes-node-app
```
This starter application code contains all the necessary configuration files for local development and deployment to Kubernetes.


### 6- Deploy the application with Helm 3
The container image for the application as already been built and pushed to a public Container Registry. In this section you will deploy the starter application using Helm. Helm helps you manage Kubernetes applications through Helm Charts, which helps define, install, and upgrade even the most complex Kubernetes application.

1- Define an environment variable named MYPROJECT and set the name of the application by replacing the placeholder with your initials:
```
export MYPROJECT=<your-initials>kubenodeapp
```
2- Identify your cluster:
```
ibmcloud ks cluster ls
```

3- Initialize the variable with the cluster name

```
export MYCLUSTER=<CLUSTER_NAME>
```

4- Initialize the kubectl cli environment
```
ibmcloud ks cluster config --cluster $MYCLUSTER
```

5- You can either use the default Kubernetes namespace or create a new namespace for this application.

If you wish to use the default Kubernetes namespace, run the below command to set an environment variable
```
export KUBERNETES_NAMESPACE=default
```


