# Guide on how to create a Webhook between GitHub and Jenkins

### Setting up the Webhook in GitHub
1. Go to your GitHub repository where you have saved your apps folder.
2. Go to Settings for that repo
3. In the navigation tab, go to Webhooks
4. In Webhooks, select Add Webhook  
![](images/webhook1.png)
5. Enter the payload URL: http://<Jenkins IP:8080>/github-webhook/ 
6. Content Type - application/JSON
7. Select individual events from list - Pushes, Pull requests
8. Add Webhook  
![](images/webhook2.png)

### Creating Jenkins Job
1. Go to Jenkins and on the main page select New Item  
![](images/webhook3.png)
2. Enter the name of Job
3. Select Freestyle
4. Select Ok  
![](images/webhook4.png)
5. Under General first fill out the description
6. In Discard old Builds - Max # = 3
7. GitHub Project - Project URL - HTTPS URL from your GitHub repo  
![](images/webhook5.png)
8. In Office 365 Connector, select Restrict where this project can be run
9. For the label, type in the name of the agent node you use.  
![](images/webhook6.png)
10. In Source Code Management, select Git
11. In repo URL, paste in the SSH URL from GitHub
12. Credentials, select add
    1. For Kind, select SSH username and private key
    2. Username - naming convention
    3. Private Key - Enter Directly - Add  
![](images/webhook8.png)
13. Branch Specifier - */main  
![](images/webhook7.png)
14. Under Build Triggers, Select GitHub hook trigger
15. Under Build Environment, select Provide Node & npm  
![](images/webhook9.png)
16. Under Build, select Add step - Execute Shell
17. Type in the shell commands you wish to run
18. Apply
19. Save  
![](images/webhook10.png)

