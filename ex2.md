## Exercise 2 - Install IBM Cloud Operator from Operator Hub
Let's understand exactly how Operators work. In the first exercise, you deployed a simple application using a DeploymentConfig and Pods -- these are "default resources" that come with OpenShift. A custom resource definition (CRD) allows you to create resources that are not necessarily running within Kubernetes, such as an IBM Cloud service. Operators manage the lifecycle of resources and create CRDs, allowing you to manage custom resources the native "Kubernetes" way.
The IBM Cloud Operator provides a simple Kubernetes CRD-Based API to provision and bind IBM public cloud services on your Kubernetes cluster. With this operator, you can simply provide service and binding custom resources as part of your Kubernetes application templates and let the operator reconciliation logic ensure that the required services and credentials are automatically created and available for your application.
1.	Navigate to your OpenShift web console, access the Administrator perspective, and click Operators > OperatorHub.
If you don't have the OpenShift web console open, you can open it by clicking here.
<br> ![image](https://user-images.githubusercontent.com/36239840/124449851-e6ae1a00-dd94-11eb-9b67-b053e4d00615.png)<br>

2.	Select Cloud Provider from the menu on left side of page and then click the IBM Cloud Operator tile.
Note: You might be presented with a disclaimer regarding support of the operator from Red Hat. If you are, click Continue.
3.	Click Install.
 <br>![image](https://user-images.githubusercontent.com/36239840/124449926-fb8aad80-dd94-11eb-94af-b8da29664d5a.png)<br>
4.	Click Install on the Operator subscription page.
The defaults are sufficient for this lab. In some cases, you might want to only install an operator for a specific namespace.
 <br>![image](https://user-images.githubusercontent.com/36239840/124450002-0f361400-dd95-11eb-87fc-558f670b9517.png)<br>
It might take a minute for the subscription to finalize. Once the installation process completes, click the View Operator button.
 <br>![image](https://user-images.githubusercontent.com/36239840/124450141-2ffe6980-dd95-11eb-85a7-82c83c5b7764.png)<br>
The Operator Details page shows more information about the operator.
 <br>![image](https://user-images.githubusercontent.com/36239840/124450188-3d1b5880-dd95-11eb-990a-dbd6409a7be3.png)<br>
Next, you need to set your IBM Cloud credentials so that the Operator knows how and where to create your Cloudant service. The operator needs to create the service in your own account, rather than the shared IBM lab account. You can learn more out this process here.
5.	Log into IBM Cloud with your account. Pick your account not the IBM lab account.
Note: You need to create the free "Lite" instance of cloudant in your personal IBM Cloud account. Do NOT select DTE Cloud Platform (aeb2e9f6f29f41b99ce8e98c1c73e611) <-> 2029624 as you do not have the appropriate permissions in that account.
```
ibmcloud login -r ##OPENSHIFT.region##
```
6.	Set your CF org, space and resource group where the Cloudant service is created.
The resource group is usually named default or Default -- case-sensitive. Note: If you renamed your default resource group, you need to specify an existing resource group in your account. If you are prompted to select a space, select the dev space.
```
ibmcloud target --cf -g default
```
7.	Verify that all fields are set:
```
ibmcloud target
```
8.	Log in to your OpenShift cluster
```
oc login
```
9.	If project is not set to default, set cluster project to default.
```
oc project default
```
10.	Use the helper script provided by IBM to create a new API token and register it as a secret in your OpenShift cluster.
```
curl -sL https://raw.githubusercontent.com/IBM/cloud-operators/master/hack/configure-operator.sh | bash
```
Sample output:
```
secret/ibmcloud-operator-secret created
configmap/ibmcloud-operator-defaults created
+ rm -rf /tmp/tmp.FDHaUEVqxd
```
11.	Verify that all the fields in data are set for the configmap (org, region, resourceGroup and space).
```
oc get configmap/ibmcloud-operator-defaults -o yaml -n default
```
12.	Verify that all the fields in data are set for the secret (api-key and region):
```
oc get secret/ibmcloud-operator-secret -o yaml -n default
```

## <a href="https://github.com/IBMDeveloperMEA/explore-operators/blob/master/ex3.md">Next Step: Exercise 3 - Create a Cloudant service</a>
