# TabCloud UBL shared pool of users demo
 
 Demo Node app with Tableau Embed front-end showcasing how to rotate Tableau Cloud user logins with jwt auth (Connected Apps).

 This is useful for clients moving from Tableau Public to Tableau Cloud Usage Based license, who want to continue emulating the behaviour of "annonymous" user access. 
 
 The main trick here is to add as many tableau shared users as needed to cope with the fact that each user can only perform up to 600 refreshes/hour. So, each time the portal embeds a visualization, a random user is used. You may need to tweak the number of shared Tableau Cloud users, based on your expected concurrency and usage per hour 

 _Note: Sharing users in Tableau is only allowed with Usage Based License!_

 ![Alt text](architecture.png?raw=true)

How to use this app:
1) Add as many dymmy users as needed to yur Tableau Cloud Site

2) Create an environment file .env in the root folder of this repo with your own Connected App details following this syntax:
```
clientId = "<connected-app-id>"
secretId =  "<secret-id>"
secretValue = "<secret-value>"
scope = "tableau:views:embed, tableau:views:authoring"
userIds =  "system1@dummy.com, system2@dummy.com, system@dummy.com, system4@dummy.com" 
```

3) Update line 15 public/index.html with your own viz url, following this syntax:
 ```
 https://<tabcloud-pod>.online.tableau.com/t/views/<site-name>/<workbook-name>/<view-name>
 ```

5) Run this to install the necessary libs:
```
npm install
```

5) Run the Node back-end server
```
node index.js
```

5) Access the front-end at http://localhost:3000/index.html

The dashboard should load each time using a different (tableau) user 
      
