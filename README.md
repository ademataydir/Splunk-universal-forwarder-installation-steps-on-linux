## How to Install Splunk Universal Forwarder on Linux

We become a member  of the www.splunk.com site  and copy the download link of Splunk Universal Forwarder and download the  file to our computer with the wget command.

![Screenshot 2025-03-27 135817](https://github.com/user-attachments/assets/39e81454-c6a0-47bd-b8ad-32271d2e8a4b)

"wget https://download.splunk.com/products/universalforwarder/releases/9.4.0/linux/splunkforwarder-9.4.0-6b4ebe426ca6-linux-amd64.deb"

![Screenshot 2025-03-27 140306](https://github.com/user-attachments/assets/02ee54bc-acd9-4a69-97ec-340a10ee64b3)

To make sure that the file has downloaded definitively, we check the download percentage and megabyte  value from the incoming results. If zero appears, the file has not been downloaded. Even though it looks like it has landed, that downloaded file will not work. In such a case, we add the sudo command to the beginning of the command we wrote above,  run it again and download it. 

![Screenshot 2025-03-27 140433](https://github.com/user-attachments/assets/2d13f9c6-2e0f-4e83-8565-ab2fddb22717)

The file has landed in our current location. To be able to upload the file, we must be in the same location as the file that we are going to upload. Once in the same location, we can run the installation commands and start the installation process. Since the extension of the file we are going to upload is "deb",  we need to use the dpkg command and we use the -i command,  which is the upload command: sudo dpkg -i <file name> 

![Screenshot 2025-03-27 140510](https://github.com/user-attachments/assets/1cb5ae32-5fc2-41bc-b4d7-1fedbde7d98b)

When the installation completes successfully, we get the result "complete". Otherwise, there may have been a problem. 

![Screenshot 2025-03-27 140614](https://github.com/user-attachments/assets/a42fb8e1-dccb-4445-94d7-00982a6692cb)

Now, in order to be able to make adjustments related to Splunk Forwarder  , we go to the location where Splunk Forwarder is installed with the cd command: cd /opt/splunkforwarder/bin

![Screenshot 2025-03-27 140713](https://github.com/user-attachments/assets/299ad780-12d8-471e-a15c-99ed7cbda882)

Here we run the Splunk Forwarder that we have installed. sudo ./splunk start --accept-license
 
![Screenshot 2025-03-27 140803](https://github.com/user-attachments/assets/e1e6e66c-93d9-4465-8f6d-9252c83024d4)

Here, we need to create a username for Splunk Universal Forwarder  . For example, I created it as "int-1" here.

![Screenshot 2025-03-27 140826](https://github.com/user-attachments/assets/334be392-36f1-4cf3-aa7b-ee4fedfad8f9)

Here, we need to create a password with at least 8 digits for the username we created for Splunk Universal Forwarder  .

![Screenshot 2025-03-27 140908](https://github.com/user-attachments/assets/5858c205-6093-45eb-805e-a2c53102255e)

It asks us to re-enter the password we just entered. 

![Screenshot 2025-03-27 140935](https://github.com/user-attachments/assets/d4cf85f7-8d27-48f1-b83a-32ea4225442f)

After the password process, we start the Splunk Universal Forwarder. If we see the result "Done" on the screen, then everything is fine.  

![Screenshot 2025-03-27 141021](https://github.com/user-attachments/assets/282eed06-6c0d-45c8-83ad-5b7457a30cec)

Now, we need to define the place where it will send the logs to the Splunk Universal Forwarder we have installed. To do this, while still in the same location,  we type the command sudo ./splunk add forward-server 10.10.200.3:9997 -auth and say Enter.

Added forwarding to ... The inscription indicates that the transaction was successful..

![image](https://github.com/user-attachments/assets/0cb27bdf-0ae6-45ea-81ea-479e0a9bf593)

Now, we need to define which logs we will send to the Splunk Universal Forwarder we have installed. For this, while still in the same position, in order;
- sudo ./splunk add monitor /var/log/syslog

![image](https://github.com/user-attachments/assets/d2023e6d-baa7-42a5-80f2-26d8abc2c694)

and
- sudo ./splunk add monitor /var/log/auth.log

and say Enter.

![image](https://github.com/user-attachments/assets/931156c0-636e-45cd-8120-c6f91d5ba94d)

To check that the adjustments we have made are working successfully, we type the command sudo /opt/splunkforwarder/bin/splunk list monitor and say Enter.

![image](https://github.com/user-attachments/assets/bad51fe6-ded5-44e3-81c5-75e4168770d5)

As you can see, Splunk Universal Forwarder  monitors auth.log and syslog logs to send to Splunk Enterprise as we set up.

### If we want to uninstall Splunk Universal Forwarder

- sudo rm -rf /opt/splunkforwarder 

We remove it using the command. 

If we want to delete the residual files and logs from Splunk Universal Forwarder

- sudo rm -rf /var/log/splunk
- sudo rm -rf /var/lib/splunk
- sudo rm -rf /etc/splunkforwarder

We run these commands one at a time.

### * Now, to monitor our system more effectively, we need to create dashboards for several use cases based on the logs collected by Splunk Universal Forwarder and sent to Splunk Enterprise.

- [Splunk Use Cases & Dashboards](https://github.com/ademataydir/splunk-use-cases)

### Note
This content has been prepared for personal learning purposes related to the installation of Splunk software. All screenshots and software are the property of Splunk Inc. This page is not intended for commercial use.
