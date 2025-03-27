## How to Install Splunk Universal Forwarder on Linux

We become a member  of the www.splunk.com site  and copy the download link of Splunk Universal Forwarder and download the  file to our computer with the wget command.

"wget https://download.splunk.com/products/universalforwarder/releases/9.4.0/linux/splunkforwarder-9.4.0-6b4ebe426ca6-linux-amd64.deb"

![image](https://github.com/user-attachments/assets/e3e1b4b2-6bcf-43de-8d67-e2b30e8b685e)

To make sure that the file has downloaded definitively, we check the download percentage and megabyte  value from the incoming results. If zero appears, the file has not been downloaded. Even though it looks like it has landed, that downloaded file will not work. In such a case, we add the sudo command to the beginning of the command we wrote above,  run it again and download it. 

![image](https://github.com/user-attachments/assets/37988058-11e2-4f9f-95bc-fd8395a1a28b)

The file has landed in our current location. To be able to upload the file, we must be in the same location as the file that we are going to upload. Once in the same location, we can run the installation commands and start the installation process. Since the extension of the file we are going to upload is "deb",  we need to use the dpkg command and we use the -i command,  which is the upload command: sudo dpkg -i <file name> 

![image](https://github.com/user-attachments/assets/2ac3fcae-8adf-414f-8483-edfe5904a832)

When the installation completes successfully, we get the result "complete". Otherwise, there may have been a problem. 

![image](https://github.com/user-attachments/assets/458ddd2a-88ca-4acf-9746-0614d944200a)

Now, in order to be able to make adjustments related to Splunk Forwarder  , we go to the location where Splunk Forwarder is installed with the cd command: cd /opt/splunkforwarder/bin

![image](https://github.com/user-attachments/assets/09111c60-b75e-4b0d-88ed-21699de37f72)

Here we run the Splunk Forwarder that we have installed. sudo ./splunk start --accept-license
 
![image](https://github.com/user-attachments/assets/9b8da2e0-2c02-4623-a58c-2c4e27f38c85)

Here, we need to create a username for Splunk Universal Forwarder  . For example, I created it as "int-1" here.

![image](https://github.com/user-attachments/assets/848cfffd-b0c3-449b-8c0b-db42c219edac)

Here, we need to create a password with at least 8 digits for the username we created for Splunk Universal Forwarder  .

![image](https://github.com/user-attachments/assets/3d393df8-1c29-4fcc-bfd9-f10a4c5a2048)

It asks us to re-enter the password we just entered. 

![image](https://github.com/user-attachments/assets/2a229842-004b-4e3b-b393-6df595fa8186)

After the password process, we start the Splunk Universal Forwarder. If we see the result "Done" on the screen, then everything is fine.  

![image](https://github.com/user-attachments/assets/0d67be86-11df-47bd-8c98-19678334fa54)

Now, we need to define the place where it will send the logs to the Splunk Universal Forwarder we have installed. To do this, while still in the same location,  we type the command sudo ./splunk add forward-server 10.10.200.3:9997 -auth and say Enter.

![image](https://github.com/user-attachments/assets/a6f1d4ca-ab35-4e3a-bedb-b2df3816d125)

Added forwarding to ... The inscription indicates that the transaction was successful..

![image](https://github.com/user-attachments/assets/0d59ad5c-3e90-4d3e-bde7-01dbf7fdcb84)

Now, we need to define which logs we will send to the Splunk Universal Forwarder we have installed. For this, while still in the same position, in order;
sudo ./splunk add monitor /var/log/syslog
and
sudo ./splunk add monitor /var/log/auth.log
and say Enter.

![image](https://github.com/user-attachments/assets/0fb3d245-aa49-4d21-9285-08b4aa4b80fc)

To check that the adjustments we have made are working successfully, we type the command sudo /opt/splunkforwarder/bin/splunk list monitor and say Enter.

![image](https://github.com/user-attachments/assets/6ad7729d-3eaa-42dc-b227-c923d7023d34)

As you can see, Splunk Universal Forwarder  monitors auth.log and syslog logs to send to Splunk Enterprise as we set up.

![image](https://github.com/user-attachments/assets/0d806ad1-36a9-4c49-b125-1162c006b06d)

If we want to uninstall Splunk Universal Forwarder

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
