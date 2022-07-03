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
### CI Architectural Diagram
![CD_Arch_Diagram](/images/cd-diagram.png)

<TODO:  Instructions for running the Python project.  How could a user with no context run this project without asking you for any help.  Include screenshots with explicit steps to create that work. Be sure to at least include the following screenshots:

* Project running on Azure App Service

* Project cloned into Azure Cloud Shell

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


