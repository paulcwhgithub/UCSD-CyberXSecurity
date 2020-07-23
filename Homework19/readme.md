## Unit 19 Homework: Protecting VSI from Future Attacks

### Scenario

In the previous class,  you set up your SOC and monitored attacks from JobeCorp. Now, you will need to design mitigation strategies to protect VSI from future attacks. 

You are tasked with using your findings from the Master of SOC activity to answer questions about mitigation strategies.

### System Requirements 

You will be using the Splunk app located in the Ubuntu VM.

### Logs

Use the same log files you used during the Master of SOC activity:

- [Windows Logs](resources/windows_server_logs.csv)
- [Windows Attack Logs](resources/windows_server_attack_logs.csv)
- [Apache Webserver Logs](resources/apache_logs.txt	)
- [Apache Webserver Attack Logs](resources/apache_attack_logs.txt	)

---

### Part 1: Windows Server Attack

![](images/19-1.png) 
#### Question 1
- Several users were impacted during the attack on March 25th.
![](images/19-2.png)
![](images/19-3.png)
  - **ANSWER: user_a and user_k**
- Based on the attack signatures, what mitigations would you recommend to protect each user account? Provide global mitigations that the whole company can use and individual mitigations that are specific to each user.
![](images/19-4.png)
![](images/19-5.png)
  - **ANSWER:**
    - **Global mitigation:**
      - **use of stateful firewall and deploy IDS and IPS solution to detect and block the instrusions**
      - **don't use email address or name as userid that can be obtained by social engineering**
      - **enforcing password policies like enforcing password history, password age, complexity requirement.**
    
    - **Individual mitigation:**
      - **allow login only from certain IP addresses**
      - **assign unique login URLs to blocks of users so that not all users can access the site from the same URL.**
      - **assign different password policies and lockout time for differnt type of users**
    
#### Question 2
- VSI has insider information that JobeCorp attempted to target users by sending "Bad Logins" to lock out every user.
- What sort of mitigation could you use to protect against this?
  - **ANSWER**
    - **instead of completely locking out an account, place it in a lockdown mode with limited capabilities.**
    - **use of multiple authentications**
    - **use a CAPTCHA to prevent automated attacks**
    - **trace of source of ip addresses with failed login and block them**
  

### Part 2: Apache Webserver Attack:
![](images/19-6.png) 
#### Question 1
- Based on the geographic map, recommend a firewall rule that the networking team should implement.
- Provide a "plain english" description of the rule.
  - **Block all incoming HTTP traffic where the source IP comes from the city of Kiev or Kharkiv in Ukraine**
- Provide a screen shot of the geographic map that justifies why you created this rule.
- **Before the attack**
![](images/19-7.png)
![](images/19-8.png)

- **After the attack**
![](images/19-9.png)
![](images/19-10.png)
  
#### Question 2

- VSI has insider information that JobeCorp will launch the same webserver attack but use a different IP each time in order to avoid being stopped by the rule you just created.

- What other rules can you create to protect VSI from attacks against your webserver?
  - **Block all incoming HTTP traffic where the user agent is Mozilla/4.0 (compatible; MSIE 6.0; Windows NT 5.2; SV1; .NET CLR 2.0.50727987787; InfoPath.1) or Chef Client/10.18.2 (ruby-1.9.3-p327; ohai-6.16.0; x86_64-linux; +http://opscode.com)**
  
  **Before the attack**
![](images/19-11.png)

**After the attack**
![](images/19-12.png)
  

