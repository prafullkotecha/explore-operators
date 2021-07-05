## Exercise 4 - Configure Application to Use Cloudant
The last step is to configure the Patient Health application front end to use the new database back end application.
1.	Access the pateinet-ui application.
<br>![image](https://user-images.githubusercontent.com/36239840/124464525-5926f600-dda5-11eb-8924-5fba90de8973.png)<br>
2.	Click the Settings link in the application.
<br>![image](https://user-images.githubusercontent.com/36239840/124464562-6512b800-dda5-11eb-97db-25d328f4c2c1.png)<br>
3.	Enter the route below into the URL entry field.
```
http://patient-db:8080/
```
<br>![image](https://user-images.githubusercontent.com/36239840/124464593-70fe7a00-dda5-11eb-80a9-525dc9a44b1e.png)<br>
4.	Click the node tile to create the connection.
<br>![image](https://user-images.githubusercontent.com/36239840/124464636-7cea3c00-dda5-11eb-928d-fe7a886f78c8.png)<br>
The frontend patient-ui application can talk to the backend patient-db without the network request leaving the cluster, thus you don't need to expose the application using the oc expose command. Kubernetes keeps an internal DNS record of the services which resolve to the IPs of the running application.<br>
Your application is now backed by the mock patient data in the Cloudant DB! You can log-in using any user-id/password in the Cloudant DB.
5.	Log in to the application using the name: opall and password: opall.
opall
<br>![image](https://user-images.githubusercontent.com/36239840/124464682-8b385800-dda5-11eb-948c-5c3ba66da6be.png)<br>
Note: if you try using a random ID and password like in Lab 1, you notice you cannot log in to the application.
<br>![image](https://user-images.githubusercontent.com/36239840/124464717-97bcb080-dda5-11eb-9884-e7be62b4833a.png)<br>
Before we complete this lab, explore the Cloudant database we are using to store these IDs and passwords.
6.	Verify you are in your account in the IBM Cloud portal.
<br>![image](https://user-images.githubusercontent.com/36239840/124464753-a1deaf00-dda5-11eb-92cc-6ad783cdda55.png)<br>
7.	Click the cloudant-service link.
<br>![image](https://user-images.githubusercontent.com/36239840/124464814-b28f2500-dda5-11eb-9cec-1b721e82bc7d.png)<br>
8.	Click Launch Cloudant Dashboard.
<br>![image](https://user-images.githubusercontent.com/36239840/124464862-c0dd4100-dda5-11eb-84cc-242b53c4babd.png)<br>
9.	Click the patients DB.
<br>![image](https://user-images.githubusercontent.com/36239840/124464909-cdfa3000-dda5-11eb-8b5f-35abecede9c1.png)<br>
10.	Explore the list of user IDs and passwords that are available to log in to the application using the {}JSON tab.
Note: in a real-world application, these passwords should not be stored as plain-text.
<br>![image](https://user-images.githubusercontent.com/36239840/124464954-deaaa600-dda5-11eb-8272-899b46d14da9.png)<br>

