# Nessus
![image](https://github.com/Sismahil/Nessus/assets/121772702/ae526184-6adc-4705-a816-5dcbf6b2c029)


<h1>Introduction</h1>
This lab shows how I set up and configured Nessus Essential to perform credentialed vulnerability scans against a Windows 10 host. In which I was able to discover, prioritize, and verify vulnerabilities that can be exploited on the system. <br />

<h2>Environments and Technologies Used</h2>

- Nessus Essential
- VMware
- Windows 10

<h2>Operating Systems Used </h2>

- Windows Server 2022
- Windows 10 

<h2>Setups</h2>

<p>
  
</p>
<p>
Step 1: download and set up Nessus Essential. connect it via SSL and create an account while inputting the activation code for verification.
</p>
</p>
<p>
Step 2: set up a new Virtual Machine on VMware by adding a Windows 10 ISO file as the installer. Also, bridge the network connection directly to the physical network
</p>
<p>

![image](https://github.com/Sismahil/Nessus/assets/121772702/4b77c8d1-f8ae-498f-8ed7-4acc35314ad4)
</p>
<p>




  
Step 3: Once windows 10 is installed on the Vm.then ping the Vm's IP address unto the command prompt of your PC to ensure connectivity with the Vm. we should notice a "Request Timed Out"
</p>
<p>

![image](https://github.com/Sismahil/Nessus/assets/121772702/8d1d59dd-db06-4323-8439-7f0d18bdb6eb)
  
</p>
Step 4: The next thing is to disable the Windows Defender firewall on our Vm by turning off our domain, private, and public profile. Immediately, we should notice our ping reply on the PC.
</p>
<p>

![image](https://github.com/Sismahil/Nessus/assets/121772702/66499224-ceb6-4d8d-ba2e-4740483493c8)

</p>
<p>
Step 5: Go to Nessus Essential to create a new scan by clicking on Basic Network Scan while filling up the name and adding the Vm's IP address as the target. Also, enable all ports scan on Nessus setting.
</p>
<p>

</p>
<p>
Step 6: Launch it to inspect our first scan without credentials to notice some basic results vulnerabilities on the Vm. Next, is to set up the Vm to accept authenticated scans by enabling the remote registry to look for insecure configuration. Also, we need to make sure our file and printer-sharing setting is enabled on the Vm. 
</p>
<p>
Step 7:  we will connect to the registry and add a key that is supposed to further disable the user account control remote account we will be using to connect to the computer during our scan by going to the registry editor to create a Dword folder called (LocalAccountFilterPolicy) and changing the value data to 1, Then we will restart the Vm. 
</p>
<p>
  
 ![image](https://github.com/Sismahil/Nessus/assets/121772702/2c5d5310-ad03-438d-9786-ef0358ffdac4)
</p>

<p>
Step 8: After the Vm is restarted and logged in. we will go to Nessus and configure the scan settings by adding credentials of our VM's username and password. However, install a depreciated Firefox on the VM  for vulnerability testing. Then launch the scan again for the second time. The reason behind this is to compare our first scan to the second scan for more vulnerability results because we enabled credential scanning and configured our Vm to accept remote scans. 
</p>


<h1>Observation</h1>
<p>
  
BEFORE CREDENTIALS:
  
![image](https://github.com/Sismahil/Nessus/assets/121772702/1c6aaee1-8aa2-48ad-a2df-add96c29a4c4)
</p>
</br>
</br>
</br>

<P>
AFTER CREDENTIALS:
  
  ![image](https://github.com/Sismahil/Nessus/assets/121772702/b042be8a-a3d7-422b-bacc-414689cc778f)
</P>
</br>
</br>
Note: Before adding credentials, we had 13 vulnerabilities with 1 medium level but after adding credentials we got 36 vulnerabilities with 4 Critcals because we installed a depreciated Firefox with no updated patches. which poses a high level of threat to our PC or organization that can be easily exploited by Bad-Actors. To remediate this vulnerability, we simply need to delete the old Firefox and install a new Firefox with updated patches against vulnerabilities. 
