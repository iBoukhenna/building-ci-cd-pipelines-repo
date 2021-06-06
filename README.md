[![Python application test with Github Actions](https://github.com/iBoukhenna/building-ci-cd-pipelines-repo/actions/workflows/main.yml/badge.svg)](https://github.com/iBoukhenna/building-ci-cd-pipelines-repo/actions/workflows/main.yml)

# Overview

Setup CI/CD Pipeline for building a Python web application and deploying it using Azure App Services.


## Project Plan

* A [Trello board] https://trello.com/b/BucwyuFR/building-ci-cd-pipelines-board
* A [Spreadsheet] https://docs.google.com/spreadsheets/d/1FLLO2Nj3flrCCnwPlZ-Jfr4BK13s3Km-g0BMFW-FouU/edit?usp=sharing


## Instructions

* Architectural Diagram

![pycharm1](imgs/building-ci-cd-pipelines-architecture.svg)

* Launch Azure Cloud Shell

![pycharm1](imgs/launch-azure-cloud-shell.PNG)

* Generate SSH key

```
ssh-keygen -t rsa
```

* Upload public key to github

![pycharm1](imgs/github-add-sshkey.PNG)

* Clone the repository using Azure Cloud Shell

```
git clone git@github.com:iBoukhenna/building-ci-cd-pipelines-repo.git
```

* Change into the new directory

```
cd building-ci-cd-pipelines-repo
```

![pycharm1](imgs/project-cloned-into-azure-cloud-shell.PNG)

* Create a new python virtual environnement

```
python -m venv building-ci-cd-pipelines-venv
```

* Activate the virtual environment

```
. building-ci-cd-pipelines-venv/bin/activate
```

![pycharm1](imgs/create-venv.PNG)

* Install dependencies and build the app

```
make all
```

![pycharm1](imgs/make-all-b.PNG)

![pycharm1](imgs/make-all-e.PNG)

* Start the application in the local environment

```
python app.py
```

![pycharm1](imgs/local-run-app.PNG)

* Open a separate Cloud Shell and test that the app is working

```
./make_prediction.sh
```

![pycharm1](imgs/local-prediction.PNG)

* Create Azure App Service

```
az webapp up --sku F1 -n building-ci-cd-pipelines-asa
```

![pycharm1](imgs/azure-app-service.PNG)

* Create the Pipeline in Azure DevOps

1. Go to https://dev.azure.com and sign in.
2. Create a new private project.
3. Under Project Settings create a new service connection and select Azure Resource Manager.
4. Create a Python-specific pipeline to deploy to App Service, and select your GitHub repo.

![pycharm1](imgs/azure-devops-pipelines.PNG)

* Get app logs

```
az webapp log tail
```

![pycharm1](imgs/log-b.PNG)

* Test the app is up and running

```
./make_predict_azure_app.sh
```

![pycharm1](imgs/azure-prediction.PNG)


![pycharm1](imgs/running-on-aas.PNG)

* Output of streamed log files

![pycharm1](imgs/log-a.PNG)

## Enhancements

<TODO: A short description of how to improve the project in the future>

## Demo 

<TODO: Add link Screencast on YouTube>


