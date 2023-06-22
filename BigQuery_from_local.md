# Use BigQuery from local development
- Using Anaconda or VSCode (jupyter in both)

## 1) Anaconda: installing google-cloud-bigquery
from google.cloud import bigquery   
to run `conda install google-cloud-bigquery` properly    
be sure to add conda-forge as a channel:
1. open conda powershell
2. to check: conda config --show channels
3. if not present: conda config --add channels conda-forge
    - https://conda-forge.org/
4. change conda env: conda activate __env_name__
5. conda install google-cloud-bigquery
- to install in python: `pip install google-cloud-bigquery` should be enough

## 2) CLient to work (project string)
Install Google Cloud SDK Shell .. make local auth-credentials?
put Client(str) .. str whatever work for first

## Job to work .. valid project ID..
in this case 'service -account' and make a project
- https://stackoverflow.com/questions/72823768/connecting-to-bigquery-by-python-projectid-and-datasetid-must-be-non-empty
- https://developers.google.com/identity/protocols/oauth2/service-account
    - `Service Account Page`
- https://console.cloud.google.com/iam-admin/iam?orgonly=true&project=jmproject86385&supportedpurview=project
- https://cloud.google.com/iam/docs/service-account-overview?_ga=2.90945628.-711726092.1682168229

To get the projectID (what to put as a string in Client)
you can see in 
https://console.cloud.google.com/iam-admin/settings?project=jmproject86385&orgonly=true&supportedpurview=project
or open Google Cloud SDK Shell (app installed early), and run:
gcloud projects list
