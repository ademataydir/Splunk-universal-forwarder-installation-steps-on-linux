## How to Install Splunk Universal Forwarder on Linux

We become a member  of the www.splunk.com site  and copy the download link of Splunk Universal Forwarder and download the  file to our computer with the wget command.

"wget https://download.splunk.com/products/universalforwarder/releases/9.4.0/linux/splunkforwarder-9.4.0-6b4ebe426ca6-linux-amd64.deb"

![image](https://github.com/user-attachments/assets/11d1c6fb-33e8-4d3a-8576-d27926975f73)

To make sure that the file has downloaded definitively, we check the download percentage and megabyte  value from the incoming results. If zero appears, the file has not been downloaded. Even though it looks like it has landed, that downloaded file will not work. In such a case, we add the sudo command to the beginning of the command we wrote above,  run it again and download it. 

![image](https://github.com/user-attachments/assets/b10deb58-eab3-41b1-8f1d-68c328e29585)

The file has landed in our current location. To be able to upload the file, we must be in the same location as the file that we are going to upload. Once in the same location, we can run the installation commands and start the installation process. Since the extension of the file we are going to upload is "deb",  we need to use the dpkg command and we use the -i command,  which is the upload command: sudo dpkg -i <file name> 

![image](https://github.com/user-attachments/assets/15d4aa6a-16a5-4c4e-96bd-2b024dc17146)

When the installation completes successfully, we get the result "complete". Otherwise, there may have been a problem. 

![image](https://github.com/user-attachments/assets/9f6b90c5-7248-481d-88a2-a8e62707fdd3)

Now, in order to be able to make adjustments related to Splunk Forwarder  , we go to the location where Splunk Forwarder is installed with the cd command: cd /opt/splunkforwarder/bin

 ![image](https://github.com/user-attachments/assets/16ddb40c-cc98-4bf5-9616-8669a75ebc4b)

Here we run the Splunk Forwarder that we have installed. sudo ./splunk start --accept-license
 
![image](https://github.com/user-attachments/assets/e8deff1b-f810-4bea-9c7e-f881cdf4a082)

Here, we need to create a username for Splunk Universal Forwarder  . For example, I created it as "int-1" here.

![image](https://github.com/user-attachments/assets/0aa7df0d-6d2e-48db-99f3-b301edc506c0)

Here, we need to create a password with at least 8 digits for the username we created for Splunk Universal Forwarder  .

![image](https://github.com/user-attachments/assets/f282ef8a-063b-4673-a128-43f9bdb13c9b)

It asks us to re-enter the password we just entered. 

![image](https://github.com/user-attachments/assets/ecefa8c6-3e52-453d-aae2-a3fe0af8319e)

After the password process, we start the Splunk Universal Forwarder. If we see the result "Done" on the screen, then everything is fine.  

![image](https://github.com/user-attachments/assets/3853f73e-5ffc-48e5-a9bd-4fc5918a741e)

Now, we need to define the place where it will send the logs to the Splunk Universal Forwarder we have installed. To do this, while still in the same location,  we type the command sudo ./splunk add forward-server 10.10.200.3:9997 -auth and say Enter.

![image](https://github.com/user-attachments/assets/053b9c20-8bd5-47d4-9d44-5eed1de11fd4)

Added forwarding to ... The inscription indicates that the transaction was successful..

![image](https://github.com/user-attachments/assets/d0b376cb-9099-4bb8-ad6e-86c7bfb9f05d)

Now, we need to define which logs we will send to the Splunk Universal Forwarder we have installed. For this, while still in the same position, in order;
sudo ./splunk add monitor /var/log/syslog
and
sudo ./splunk add monitor /var/log/auth.log
and say Enter.

![image](https://github.com/user-attachments/assets/e8e9c3c7-4692-4afc-b231-1754d2a225ca)

To check that the adjustments we have made are working successfully, we type the command sudo /opt/splunkforwarder/bin/splunk list monitor and say Enter.

![image](https://github.com/user-attachments/assets/24d99eef-2551-4119-936f-a55e49945257)

As you can see, Splunk Universal Forwarder  monitors auth.log and syslog logs to send to Splunk Enterprise as we set up.

![image](https://github.com/user-attachments/assets/9948e81c-a23f-4f2d-9718-a5b1c73a06a0)

If we want to uninstall Splunk Universal Forwarder
;sudo rm -rf /opt/splunkforwarder We remove it using the command. 
If we want to delete the residual files and logs from Splunk Universal Forwarder;
sudo rm -rf /var/log/splunk
sudo rm -rf /var/lib/splunk
sudo rm -rf /etc/splunkforwarder We run these commands one at a time.

### Note
This content has been prepared for personal learning purposes related to the installation of Splunk software. All screenshots and software are the property of Splunk Inc. This page is not intended for commercial use.
