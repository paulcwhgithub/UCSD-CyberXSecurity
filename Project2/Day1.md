### Instructions

Complete the following to find the flag:

- Discover the IP address of the Linux web server.
  - **Answer**: '> nmap -A 192.168.1.1/24'
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
