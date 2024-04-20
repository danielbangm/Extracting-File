<p align="center">
<img src="https://shorturl.at/kDMN6" />
</p>

<h1>Setup map in Azure sentinel with Latitude and Longitude</h1>

I will download a powershell script from github to run in our Honeypot virtual machine to capture all event logs. For that, we will turn off windows defender firewall on vm first.

<h2>Objectives</h2>

-  Understanding event logs
-  Understanding the use of windows Defender Firewall
-  Gain a better understanding of how to run a script with powershell ISE

<h2>Environments and Technologies Used</h2>

- Virtual Machine(Honeypot-vm)
- Windows Defender Firewall
- Event logs
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


-  Step 3: Download the powershell script and sign up for ipgeolocalisation.io

I downloaded this <a href="https://github.com/joshmadakor1/Sentinel-Lab/blob/main/Custom_Security_Log_Exporter.ps1">Powershell Script</a> which is essentially a github repository. Click on the custom securitylog exporter, either download or just copy it and then open powershell ISE on the VM. Create new file and paste it, save it on the desktop as "log exporter.The only thing to modify on that scrip is the API key. In order to get that, we have to sign up for ipgeolocalisation.io and get our API key replaced in the powershell script
![image](https://github.com/danielbangm/map-in-sentinel/assets/22795502/ea1fef18-f0c0-49df-8258-0c24be6300bb)

-  Step 4: Run the script

After getting your own API key, launch powershell ISE and run the script in Vm. The API keyy allows us to get the geolocalisation and longitute, latitude of the attackers. Essentially what it does, it looks through the event logs, security logs, then grabs all the events of people who failed to log in and grabs their IP address, and geolocalisation data to create a new log file
![image](https://github.com/danielbangm/map-in-sentinel/assets/22795502/10569e1e-3b84-41c7-8610-99d53730836a)

- Step 5: Create a custom log in our log analytic workspaces

  I go backt to portal.azure, let's reate a custom log inside our log analytic workspace that will allow us to bring that custom log with geodata into our logs analytic workspaces. For that we also need to copy the log data from our VM located in C:\ProgramData\failed_rdp.log and paste it in a new word document in our local machine . Now let's create a custom log named "FAILED_RDP_WITH_GEO_CL"
  ![image](https://github.com/danielbangm/map-in-sentinel/assets/22795502/790d5423-6b55-4a6e-9d8a-803632558748)


