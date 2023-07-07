# TabCloud UBL shared pool of users demo
 
 Demo Node app with front-end showcasing how to rotate Tableau Cloud user logins with jwt auth (Connected Apps).

 This is useful for clients moving from Tableau Public to Tableau Cloud UBL license who want to continue emulating the behaviour of "annonymous" user access. 
 
 The main trick here is to add as many tableau shared users as needed to cope with the fact that each user can only perform up to 600 refreshes/hour.

 So, each time the portal embeds a visualization, a random user is used. 

 Note: Sharing users in Tableau is only allowed with Usage Based License 

 ![Alt text](architecture.png?raw=true)

How to use this:

1) Create an environment file .env in the root folder of this repo with your own Connected App details following this syntax:
```
clientId = "<connected-app-id>"
secretId =  "<secret-id>"
secretValue = "<secret-value>"
scope = "tableau:views:embed, tableau:views:authoring"
userIds =  "user1@company.com, user2@company.com, user3@company.com, user4@company.com" 
```
2) Add your own Tableau Viz url in line 15 of public/index.html

3) Install the necessary libs 
```
npm install
```

4) Run the Node back-end server
```
node index.js
```

5) Access the front-end at http://localhost:3000/index.html

The dashboard should load each time using a different (tableau) user 
      
