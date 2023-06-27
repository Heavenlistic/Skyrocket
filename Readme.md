# To Deploy Web Application using biceps and Pipelines on Azure devops

1.  

2. In Azure Devops > Create New Project > Project Name:  > Description: To Deploy Web Application using biceps and Pipelines on Azure devops > Advanced: Agile > Create

2. In Azure Devops > Project >Repo > Clone > Copy url > use git commands to push code from VS Code to Azure Devops

3. In Azure Devops > Project settings > Service Connections (API to connect Azure devops to Microsoft Azure) > Create Service Connections > Azure Resource manager > Service principle (automatic) > Service connection name: (azure subscription in the azure-pipelines.yml file) > select Grant access permission to all pipelines > save (ensure to authorize the Microsoft service connection request)

4. To resolve ‘no subscription’ error manually > Project settings > Service Connections > Azure Resource manager > Service principle (manual)

5. In azure > Home > Cost Management + Billing > All billing subscriptions > Azure subscription 1 > copy Subscription details (Subscription ID, Subscription Name, Tenant ID)

6. In azure > Home > Active directory > App registrations > New Registration > Name: (azureSubscription name in pipeline.yml) > Supported account types: Select 3rd option > Register> (copy Application ID which is the same as the Service Principal ID for manual service connection)

7. Active directory > App registrations > (new subscription name) > Certificates & secrets > New client secret > Description: Azure devops Service Connection > Expires : 12mths > Add > (copy Value & paste as Service principal key, copy in notepad since its available only once)

8. Home > Subscription > Azure subscription 1 > Access control (IAM) > Add role assignment > Privileged administrator roles > Contributor > Select members: (new subscription name) > Next > Review +assign

9. In Azure Devops > Files > Pipelines > Create Pipeline > Azure Repos Git > Select Project > Existing Azure Pipeline YAML file > Select Path > Continue > Save > Run pipeline

10. Pipelines > Select pipeline > Run pipeline > Job > (if there is error, select the error e.g., Preview Bicep Changes shows error “Could not find a part of the path”. In Vs Code > azure-pipeline.yml file > on line 10 template file > change path to main/webapp.bicep > git add . > git commit -m "initial commit > git push)

11. Pipelines > Select pipeline (e.g., skyrocket) > Run pipeline > Job > (if there is error, select the error e.g., Preview Bicep Changes shows error “No available instances to satisfy this request. App Service is attempting to increase capacity”, delete all other resource groups in Azure. In Vs Code > azure-pipeline.yml file > on line 7 , make changes to resource group name >  on line 8, change location  > git add . > git commit -m "initial commit > git push)

12. Pipelines > Select pipeline > Run pipeline > Job >  (if there is error, select the error e.g., Preview Bicep Changes shows error “Deployment 'webapp' could not be found.  Delete all other resource groups in Azure again. In Vs Code > webapp.bicep > on line 7  make changes to websitename > git add . > git commit -m "second commit > git push)

13. In MS Azure > Resourcegroup  > App Service > Browse or Default domain (to confirm website has been successfully deployed) 






# Commands
1. git config --global user.name <username>
2. git config --global user.email <email>
3. git config --global --unset-all user.name (to resolve error of multiple values)
4. git init > git add . > git commit -m "initial commit"
5. git remote set-url origin <new_url> (to change git remote origin)
6. git remote -v (to show the origin of the project) 
7. git remote add origin (git link) 
   git branch -M main 
   git push -u origin --all
8. git add . > git commit -m "Second commit" > git push (for updated changes)
