{"title":"Heroku Deployment","weight":"40"} 

# Heroku Deployment

## Pre-requisites

Before deploying to Heroku, you will need to have the heroku gem installed. If you don't have that already installed, Studio will prompt you to install it before deploying to heroku. You will also need a Ruby on Rails project opened in Studio before you can proceed with the deployment.

## Deploying to Heroku

Once you have a Ruby on Rails project opened in Studio, you should be able deploy the project using the deployment wizard. Click on the box icon in the App Explorer and select "Run Deploy Wizard" (Shown below).

![Deploy_Wizard](/Images/appc/download/attachments/30083203/Deploy_Wizard.png)

In the deployment wizard, select the Heroku option and follow the steps to login and deploy your project. After you have finished running through the wizard, the "git push heroku master" command will run in the Studio terminal which deploys your project to heroku. After you have done the initial deployment to Heroku, clicking on the box icon again will allow you to select a number of Heroku commands (Shown below).

![Heroku_Deploy](/Images/appc/download/attachments/30083203/Heroku_Deploy.png)