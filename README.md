# Overview
This project shows the steps on how to build a CI pipeline using Github actions and a CI/CD pipeline using Azure Devops.
## Part 1
Use a HelloWorld python script and test script to demonstrate using Github actions for CI

## Part 2
Deploy a Pyhon ML Flask Application to Azure App Services through Azure a CI/CD pipeline


## Project Plan
* [Trello board for the project tasks](https://trello.com/b/XvIAQub8/nd-ci-cd-project)
* [Spreadsheet for project plan](https://docs.google.com/spreadsheets/d/1zbUaBiTaXJB7IBoyU8Xqysn9V-tIMATd08ThGbKKnaE/edit?usp=sharing)

## Instructions

### CI Architectural Diagram
![CI_Arch_Diagram](/images/ci-diagram.png)
### CD Architectural Diagram
![CD_Arch_Diagram](/images/cd-diagram.png)

### Setup Environment
1) Setup Azure Cloud Shell
![AzureShell](/images/Start-Azure-Cloud-Shell.png)

2) Generate SSH keys on cloud shell and copy key to github repo to be able to clone the project
    * [Instructions for genererations of SSH keys](https://docs.github.com/en/authentication/connecting-to-github-with-ssh/generating-a-new-ssh-key-and-adding-it-to-the-ssh-agent)  
    * [Instructions for adding keys to Github account](https://docs.github.com/en/authentication/connecting-to-github-with-ssh/adding-a-new-ssh-key-to-your-github-account)

3) Clone Repo to Azure cloud shell
![CloneRepo](/images/Clone-Repo.png)

### CI using GitHub actions

1) Navigate to hello-world-app directory
    ```bash
    cd hello-world-app
    ```
2) Locally test the hello-world-app
    *  Setup a Python Virtual Environment ``` python3 -m venv ~/.azure-ci ``` from the root of the Azure Cloud Shell
    *  Run the virtual Environment ``` source ~/.azure-ci/bin/activate ```
    *  Run ``` make all ``` to install requirements, test and lint the application 
    ![CI_InstallRequirements](/images/CI_InstallRequirements.png)
    ![CI_LocalTest](/images/CI_LocalTest.png)
3) Github Actions [workflow yml file](https://github.com/mo-badreldin/nd082-azure-devops-project/blob/main/.github/workflows/pythonapp.yml) is added to the repo to setup CI pipeline
    * The yml include info about the environment setup, the trigger of the pipeline and the steps for the CI pipeline
 4) Any new commit to the repo will trigger the CI pipeline 
 5) Under [GitHub Actions](https://github.com/mo-badreldin/nd082-azure-devops-project/actions), The pipleine previous runs and the status of each run could be seen
    ![CI_PipelineOverview](/images/CI_PipelineOverview.png)
 7) Under each run, the details of the pipeline steps and the results could be seen
    ![Github_Actions](/images/Github_Actions.png)


### WebApp using Azure App Services
1) Navigate to project root directory

2) Deploy a new Azure webapp (Detailed Info in [Microsoft Docs](https://docs.microsoft.com/en-us/azure/app-service/quickstart-python?tabs=flask%2Cwindows%2Cazure-cli%2Cvscode-deploy%2Cdeploy-instructions-azportal%2Cterminal-bash%2Cdeploy-instructions-zip-azcli))
    * Setup a Python Virtual Environment ``` python3 -m venv ~/.azure-cd ``` from the root of the Azure Cloud Shell
    * Run the virtual Environment ``` source ~/.azure-cd/bin/activate ```
    * Run ``` make install ``` to install requirements
    * Create an app service and deploy the app ``` az webapp up -n <app-name> -g <resource-group-name> -l <location> --sku B1 ```
    * In Azure Portal, check the deployment of the app under App Services
        ![CD_AppServices](/images/CD_AppServices.png) 
    * Verify deployment by visiting URL ``` https://<app-name>.azurewebsites.net/ ```
        ![CD_WebAppURL](/images/CD_WebAppURL.png)

3) Perform Prediction
    * Edit ``` ./make_predict_azure_app.sh ``` to update the name of app in ``` -X POST https://<yourappname>.azurewebsites.net:$PORT/predict ```
    * Execute ``` ./make_predict_azure_app.sh ```
    * If app is deployed and working correctly then you should get prediction result
        ![CD_PredictionResult](/images/CD_PredictionResult.png)

### CD using Azure Pipeline (Detailed Info in [Microsoft Docs](https://docs.microsoft.com/en-us/azure/devops/pipelines/ecosystems/python-webapp?view=azure-devops&WT.mc_id=udacity_learn-wwl))  
1) From Azure Portal navigate to Azure DevOps and create a new Azure DevOps project
2) From project settings, set up a new service connection via Azure Resource Manager
3) In Azure DevOps project, go to pipelines to create a new pipeline
4) Choose where the soruce code is stored ***GitHub***
5) Configure Pipeline to ***Python to Linux Web App on Azure***
6) In Azure DevOps Project the pipeline should be deployed
    ![CD_PipelineOverview](/images/CD_PipelineOverview.png)
7) Inside the pipeline all previous run and their result is available
    ![CD_PipelineRuns](/images/CD_PipelineRuns.png)
8) Under each pipeline run, details of steps and result of each step could be seen
    ![CD_PipelineDetails](/images/CD_PipelineDetails.png)
9) Logs from the running application could be inspected under ``` https://<app-name>.scm.azurewebsites.net/api/logs/docker ```
    ![CD_LogFiles](/images/CD_LogFiles.png)
 
### Locust Test
![Locust_Test](/images/Locust_Test.png)

## Enhancements

* Migrate Source Code from Github to Azure DevOps repo system for easier integration of repos and pipelines
* Use Azure pipelines instead of Github Actions for both CI and CD
* Automate testing of successful deployment of webapp 

## Demo 

[Video Demo](https://youtu.be/gIgK68FxyJ0)

## Github Action Badge

[![Python application test with Github Actions](https://github.com/mo-badreldin/nd082-azure-devops-project/actions/workflows/pythonapp.yml/badge.svg?branch=main)](https://github.com/mo-badreldin/nd082-azure-devops-project/actions/workflows/pythonapp.yml)
