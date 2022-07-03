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

<TODO:  Instructions for running the Python project.  How could a user with no context run this project without asking you for any help.  Include screenshots with explicit steps to create that work. Be sure to at least include the following screenshots:

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


### CD using Azure Pipeline



* Passing tests that are displayed after running the `make all` command from the `Makefile`

* Output of a test run

* Successful deploy of the project in Azure Pipelines.  [Note the official documentation should be referred to and double checked as you setup CI/CD](https://docs.microsoft.com/en-us/azure/devops/pipelines/ecosystems/python-webapp?view=azure-devops).

* Running Azure App Service from Azure Pipelines automatic deployment

* Successful prediction from deployed flask app in Azure Cloud Shell.  [Use this file as a template for the deployed prediction](https://github.com/udacity/nd082-Azure-Cloud-DevOps-Starter-Code/blob/master/C2-AgileDevelopmentwithAzure/project/starter_files/flask-sklearn/make_predict_azure_app.sh).
The output should look similar to this:

```bash
udacity@Azure:~$ ./make_predict_azure_app.sh
Port: 443
{"prediction":[20.35373177134412]}
```

* Output of streamed log files from deployed application

> 

## Enhancements

<TODO: A short description of how to improve the project in the future>

## Demo 

<TODO: Add link Screencast on YouTube>


