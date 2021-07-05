## Exercise 3 - Create a Cloudant service
In this exercise, use the Custom Resource Definitions to create the Cloudant service. Note: Be sure the Project is set to example-health.
1.	In the OpenShift web console, return to the IBM Cloud Operator -> Operator Details page.
You'll see that there's two APIs available -- a Service and a Binding. A Service allows us to create the actual Cloudant instance.
Note: Be sure the Project is set to example-health.
<br> ![image](https://user-images.githubusercontent.com/36239840/124458919-a358a900-dd9e-11eb-82cf-2f72458f3cb9.png)<br>
2.	Click Create Instance in the Service tile.
3.	Click the YAML View radio button.
 <br>![image](https://user-images.githubusercontent.com/36239840/124458947-a9e72080-dd9e-11eb-9b42-e757fdaa2180.png)<br>
4.	Copy and replace the following YAML code:
```
apiVersion: ibmcloud.ibm.com/v1alpha1
kind: Service
metadata:
  name: cloudant-service
spec:
  plan: lite
  serviceClass: cloudantnosqldb
```
<br>![image](https://user-images.githubusercontent.com/36239840/124458975-b2d7f200-dd9e-11eb-973a-1224c1b29ab7.png)<br>
5.	Click Create
Wait a couple minutes for the service to provision and become Online.
<br>![image](https://user-images.githubusercontent.com/36239840/124459020-c2573b00-dd9e-11eb-92f3-582e34d52b45.png)<br>
The service status should change to Online as shown above. You can debug any potential issue by clicking on the service name and looking at the details provided on that page. The most typical error you will see is that you already have a Cloudant "lite" service provisoined. To work around this issue, edit the service YAML to use standard instead of Lite. Note that "Standard Cloudant" is a paid service. Another option is to navigate to your IBM Cloud dashboard and delete your existing instance of the Lite Cloudant.
6.	After verifying that there are no bugs and the service is "online", double-check the Cloudant service exists in your IBM Cloud account. Note: You might need to switch to your own account using the account drop down menu on the top-right.
<br>![image](https://user-images.githubusercontent.com/36239840/124459059-ce42fd00-dd9e-11eb-91c1-b6cb7ad8fad6.png)<br>
<br>![image](https://user-images.githubusercontent.com/36239840/124459085-d4d17480-dd9e-11eb-880a-9b4c8ff05b7e.png)<br>
 
7.	Return to the OpenShift web console and click Create Instance for Binding resource for your Operator.
Note: Be sure the Project is set to example-health.
<br>![image](https://user-images.githubusercontent.com/36239840/124459119-def37300-dd9e-11eb-95d7-af417274c378.png)<br>
8.	After switching to the YAML View, copy and paste the following YAML code into your binding definition.
```
apiVersion: ibmcloud.ibm.com/v1alpha1
kind: Binding
metadata:
  name: cloudant-binding
spec:
  serviceName: cloudant-service
``` 
9.	Click Create.
<br>![image](https://user-images.githubusercontent.com/36239840/124459163-eb77cb80-dd9e-11eb-942f-77fcef651994.png)<br>
Wait a couple minutes for the binding to provision and come Online.
<br>![image](https://user-images.githubusercontent.com/36239840/124459285-0ea27b00-dd9f-11eb-814a-848886e12259.png)<br>

10.	Click cloudant-binding and view the details of the binding.
<br>![image](https://user-images.githubusercontent.com/36239840/124459300-12ce9880-dd9f-11eb-821b-7d2ad1a462e0.png)<br>

11.	Click the Resources tab.
12.	Click the cloudant-binding link.
<br>![image](https://user-images.githubusercontent.com/36239840/124459328-18c47980-dd9f-11eb-8bf0-ac0a0f449490.png)<br>
13.	Verify your credentials for accessing your Cloudant DB. Make sure there is data securely stored in the secret.
<br>![image](https://user-images.githubusercontent.com/36239840/124459422-27ab2c00-dd9f-11eb-843f-3a3e97ef46c4.png)<br>

## <a href="https://github.com/IBMDeveloperMEA/explore-operators/blob/master/ex4.md">Next Step: Exercise 4 - Deploy new application back-end</a>
