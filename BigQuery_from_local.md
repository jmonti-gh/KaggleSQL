# Use BigQuery from local development
- Using Anaconda or VSCode (jupyter in both)

## 1) Anaconda: installing google-cloud-bigquery
Python import: __*from google.cloud import bigquery*__   
to run `conda install google-cloud-bigquery` properly    
be sure to add __*conda-forge*__ as a channel:
1. open conda powershell
2. to check: conda config --show channels
3. if not present: conda config --add channels conda-forge
    - https://conda-forge.org/
4. change conda env: conda activate __env_name__
5. conda install google-cloud-bigquery
- to install in python: `pip install google-cloud-bigquery` should be enough

## 2) bigquery.Client()
To use the Google BigQuery Service we need a google account plus valid credentials.
Google BigQuery Service provide use lot of datasets in different projects.    
Provide credentials to ADC in a local develoment enviroment, User Credentials:
1. Install and initialize the gcloud CLI.
2. Create your credential file: gcloud auth application-default login
- A login screen is displayed. After you log in, your credentials are stored in the local credential file used by ADC.
- https://cloud.google.com/docs/authentication/provide-credentials-adc#cloud-based-dev
- client = bigquery.Client()
    - OSError: Project was not passed and could not be determined from the environment.
	- You must pass an string to project method.
	- A correct string is the PROJECT_ID or the PROJECT_NUMBER
	- whatever string you pass is valid to view data but not to query
	- client = bigquery.Client('whatever')

## Valid querys - valid ProjectId
To avoid:
BadRequest: 400 POST https://bigquery.googleapis.com/bigquery/v2/projects/whatever/jobs?prettyPrint=false: ProjectId and DatasetId must be non-empty

Create a project en google:
1. login to a google account
2. got to Service Account Page
3. select CREATE PROJECT 
Get the ProjectId and the Project Number
1. open Google Cloud SDK Shell (or Cloud Tools for PowerShell)
2. run: gcloud projects list
3. get the PROJECT_ID or PROJECT_NUMBER values.
4. Use whichever of them 'as a string' in Client method:
    - client = bigquery.Client('10151058852035')
- https://developers.google.com/identity/protocols/oauth2/service-account
- https://stackoverflow.com/questions/72823768/connecting-to-bigquery-by-python-projectid-and-datasetid-must-be-non-empty
