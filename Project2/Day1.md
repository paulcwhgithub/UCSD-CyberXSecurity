## Day 1 Activity File: Red Team

### ELK Server Setup Instructions

- As the you attack a web server today, it will send all of the attack info to an ELK server.

- The following setup commands need to be run, before the attack takes place in order to make sure the server is collecting logs.

- Be sure to complete these steps before starting the attack instructions.

**Instructions**

- Double click on the 'HyperV Manager' Icon on the Desktop to open the HyperV Manager.

- Choose the `Capstone` machine from the list of Virtual Machines and double-click it to get a terminal window.

- Login to the machine using the credentials: `vagrant:tnargav`

- Switch to the root user with `sudo su`

#### Setup Filebeat

Run the following commands:
- `filebeat modules enable apache`
- `filebeat setup`

The output should look like this:

![](../../../Images/ELk-Setup/filebeat.png)

#### Setup Metricbeat

Run the following commands:
- `metricbeat modules enable apache`
- `metricbeat setup`

The output should look like this:

![](../../../Images/ELk-Setup/Metricbeat.png)

#### Setup Packetbeat

Run the following command:
- `packetbeat setup`

The output should look like this:

![](../../../Images/ELk-Setup/Packetbeat.png)

Restart all 3 services. Run the following commands:
- `systemctl restart filebeat`
- `systemctl restart metricbeat`
- `systemctl restart packetbeat`

These restart commands should not give any output:

![](../../../Images/ELk-Setup/enable.png)

Once all three of these have been enabled, close the terminal window for this machine and proceed with your attack.

---

### Attack!

Today, you will act as an offensive security Red Team to exploit a vulnerable Capstone VM.

You will need to use the following tools, in no particular order:
- Firefox
- Hydra
- Nmap
- John the Ripper
- Metasploit
- curl

### Setup

Your entire attack will take place using the `Kali Linux` Machine.

- Inside the HyperV Manager, double-click on the `Kali` machine to bring up the VM login window.

- Login with the credentials: `root:toor`

### Instructions

Complete the following to find the flag:

- Discover the IP address of the Linux web server.
  - **Answer**: '>nmap -A 192.168.1.1/24'
  - ![](images/day1-1.png)
  
- Locate the hidden directory on the web server.
  - **Answer**: 'By browsing the website http://192.168.1.105, we found there is a hidden folder inside company_folders that requires authentication'
  - ![](images/day1-2.png)
  - ![](images/day1-3.png)

- Brute force the password for the hidden directory using the hydra command:
    - **Answer**: `hydra -l ashton -P /usr/share/wordlists/rockyou.txt -s 80 -f -vV 192.168.1.105 http-get /company_folders/secret_folder`
    - ![](images/day1-4.png)
    - ![](images/day1-5.png)
    - ![](images/day1-6.png)
    
- Break the hashed password with the Crack Station website or John the Ripper.
- Connect to the server via WebDav.
    - **Answer**: Using cadaver to connect to the webdav folder
    - ![](images/day1-7.png)
    
- Upload a PHP reverse shell payload.
  - generate the payload by msfvenom
  - ![](images/day1-8.png)
  
  - Use cadaver again to put the payload to the webdav folder
  - ![](images/day1-9.png)
  - ![](images/day1-10.png)
  
- Execute payload that you uploaded to the site to open up a meterpreter session.
  - ![](images/day1-11.png)
  - ![](images/day1-12.png)
- Find and capture the flag.
  - ![](images/day1-13.png)

After you have captured the flag, show it to your instructor.

Be sure to save important files (e.g., scan results) and take screenshots as you work through the assessment. You'll use them again when creating your presentation.

---
© 2020 Trilogy Education Services, a 2U, Inc. brand. All Rights Reserved.
