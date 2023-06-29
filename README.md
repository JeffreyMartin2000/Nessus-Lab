# Nessus Lab
I wanted to learn more about vulnerability scanners and how to practice using them. Nessus is the best tool to do this. I am new to the cyber field so this has been a great experience. 
-
So I have my Windows 10 vm running and my Nessus Essentials running on my host. I ensure connectivity with the vm by disabling the firewalls(on the vm, for education purpose) and using ping to reach the vm from our host. We are just trying to make the vm accessible from Nessus. Now lets scan the machine and see what vulnerabilities pop up
<img width="959" alt="first scan no creds" src="https://github.com/JeffreyMartin2000/Nessus-Lab/assets/129632324/5a165ffc-475a-4549-8272-583b85f01ef9">
So this is without credentials set obviously. With this being a non credential scan, we can only see so much. There is a firewall vulnerability. However I want to see some criticals to see what they may look like on the CVSS score.
So there are a few things to do to enable the machine to be scanned by Nessus with credentials. Because the VM is not on our domain, these steps are needed. I will first enable the remote registery. This allows the scanner to weed through the registery to find any misconfigurations. 
<img width="960" alt="Remote Registry" src="https://github.com/JeffreyMartin2000/Nessus-Lab/assets/129632324/3c38e6f2-de6b-4367-b28d-db50eef5dd9b">
Next I set the UAC to never notify
<img width="959" alt="User Account Control" src="https://github.com/JeffreyMartin2000/Nessus-Lab/assets/129632324/f97839c6-1504-4e9c-8d07-46dd645eaac3">
And to further enable the credentialed scan, I went into the registery editor and created a DWORD value. 
<img width="713" alt="Local Account Token Filler Poilcy  DWORD value of 1" src="https://github.com/JeffreyMartin2000/Nessus-Lab/assets/129632324/936dc6f7-46cd-4458-831a-530f780fb92a">

Now lets see what the credentialed scan tells us
<img width="946" alt="creds scan" src="https://github.com/JeffreyMartin2000/Nessus-Lab/assets/129632324/cbc791cf-6781-4640-bc43-769a37128a23">
So this type of scan reveals more by trusting access into many system configurations
Here is an example of what we can see when we click a specific vulnerability
<img width="819" alt="example of critical vulnerability" src="https://github.com/JeffreyMartin2000/Nessus-Lab/assets/129632324/901e7044-4ee9-446a-a81f-783dccdb2b65">
This critical vulnerability calls for a simple update of a service. In this case, internet explorer. We can also see what the CVSS score is ont he right. Also on the bottom of the page we are notified of the port number, protocol, and ip address of the machine. 
This lab taught me how to set up an environment that allowed me to practice using Nessus. I learned what a credentialed and non-credentialed scan displayed. I also learned that Nessus shows the CVSS severity score, and how to remediate a specific vulnerability. 
