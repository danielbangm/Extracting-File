<p align="center">
<img src="https://rb.gy/4jb650" />
</p>

<h1>Watch LIVE ATTACKS on my Map Azure Sentinel</h1>

I will download a powershell script from github to run in our Honeypot virtual machine to capture all event logs. For that, we will turn off windows defender firewall on vm first.

<h2>Objectives</h2>

-  setting up map Azure Sentinel
-  Extracting fields to sort data from custom logs
-  Understanding the use of windows Defender Firewall
-  Gain a better understanding of how to run a script with powershell ISE

<h2>Environments and Technologies Used</h2>

- Virtual Machine(Honeypot-vm)
- Azure Sentil
- PowerShell ISE
- Remote Desktop

<h2>Operating Systems Used</h2>

-  Windows 10 pro

<h2>List of Prerequisites</h2>

-  All you need for this lab is the free Azure Tenant and Subscription

<h2>Installation steps</h2>

-  Step 1: Clean Up the Raw data in our custom log

Now that we have created our custom logs entries imported from our virtual machine, we have have data disorganized in our custom log analytic. We are going to sort that data by longitude, latitude, destination etc... To do that, we just click on the dropdown arrow on any log, click on the three dots and then "extract fields. Just highlight the value and call it by the corresponding field title and field type
![image](https://github.com/danielbangm/Extracting-File/assets/22795502/eb0b303d-5caf-4732-87f6-b2626ba5c701)


-  Step 2: Setting up Map in Azure Sentile

Go to portal.azure and type Azure Sentinel. From the overview you can see logs that are coming in, we can see the failed RDP with geolocation. The goal here is to set up our own map. Click on workbook, then add workbook. Click on edit, and remove the two default widgets that come with workbook. Now let's add a query and paste our  Log analytics workspace Query.
![image](https://github.com/danielbangm/Extracting-File/assets/22795502/801a74bd-b345-4e1f-9533-d692c0611997)
Now choose to vizualise it  with Map, We can even plot things in the map by country
![image](https://github.com/danielbangm/Extracting-File/assets/22795502/3131578e-f0d0-4142-a168-ec6ad487d347)


-  Step 3: Observing Live Attacks

I left my map and VM up for 48h to see if alot more attacker would try to log in to our honeypot. From the map, we can see there's so many brute forces from all over the place(China, Philippines, Taiwan, Russia, India). We can see LIVE attacks to our Virtual machine. This is just Remote Desk login attemps from all over the world because SMB is opened over the internet so no doubt people are trying to authenticate
![image](https://github.com/danielbangm/Extracting-File/assets/22795502/55b6c6b4-908e-413a-9108-ec246c79dcf2)

CONCLUSION

As soon as anythng is put on the internet, whether is your computer with a routable IP address, people with try to get into it no matter what you are, if you are a big company or a real estate property, you will be a target of attackers. We should always avoid using the username of "administrator" because that is the most guest's username trying to break into my Virtual Machine. Just try to avoid using common usernames and also use MFA and restricting RDP 
![image](https://github.com/danielbangm/Extracting-File/assets/22795502/4241b66b-f59e-4340-ad34-3dbb1342e52e)

