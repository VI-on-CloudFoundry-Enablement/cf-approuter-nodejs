# CloudFoundry AppRouter

## Overview
The approuter is responsible to manage the routes and the access to all other applications in a cloud foundry space. Basically every app could do the authentication check and so on by their own, but using a central app router has various benefits. 

## Prepare and Deploy
Go into the manifest and replace the d-user with your username or an unique id
Then build the java war package with Maven

Then push to Cloud Foundry
```
cf push
```

## Troubleshooting
### Directory not Empty
There is an error during cf push that says that the folder "node_modules" is not empty. This happens, because the node runtime tries to load the depdend modules on it's own.
The solution is that you locally delete all subfolders within node_modules beside the @sap folder and run cf push again.

### Loading modules

This repository doesn't come with the dependend nodejs modules. Therefore you have to load them first. The app router is only available in an SAP-internal repository and 
```
npm install --registry=http://nexus.wdf.sap.corp:8081/nexus/content/groups/build.milestones.npm --proxy=null
```