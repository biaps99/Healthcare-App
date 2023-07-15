# Healthcare-App
App to help doctors to quickly analyse medical images and researchers to deploy ML models

![App Architecture](./kubernetes_cluster.drawio.png "App Architecture")

## Installations

Install:

1. **Docker** - https://docs.docker.com/get-docker/
 
2. **Minikube** - https://minikube.sigs.k8s.io/docs/start/

3. **Minikube ingress** - https://kubernetes.io/docs/tasks/access-application-cluster/ingress-minikube/

4. **Terraform** - https://www.terraform.io/downloads

## Commands

Change value of **keys** and **IDs** for the **social accounts** and the value for **email** and **password** to sending emails. Assign a value for **master_key** and **master_iv** variables on **"backend/Django/container_api/scripts/cifra.py"** file and on **"backend/Django/container_api/scripts/decifra.py"**.

Open **7** command line windows:

- In the first one, run the command **"minikube start"**, go to the frontend root folder and run the commands **"yarn install"** and **"yarn build"**.

- In the second one, go to the **"kubernetes/backend_database/database/terraform_database"** folder and run the commands **"terraform init"**, **"terraform plan"** and **"terraform apply"**.

- In the third one, go to the **"kubernetes/orthanc/terraform_orthanc"** folder and run the commands **"terraform init"**, **"terraform plan"** and **"terraform apply"**.

- In the fourth one, go to the **"kubernetes/orthanc/terraform_orthanc_2"** folder and run the commands **"terraform init"**, **"terraform plan"** and **"terraform apply"**.

- In the fifth window, go to the **"kubernetes/backend_database/backend"** folder and run **"docker build backend:1 -f Dockerfile <path_to_backend_Django_root_folder>** and go to **"kubernetes/backend_database/backend/terraform_backend"** folder and run the commands **"terraform init"**, **"terraform plan"** and **"terraform apply"**.

- In the sixth window, go to the "kubernetes/frontend" folder and run **"docker build frontend:1 -f Dockerfile <path_to_frontend_root_folder>** and go to **"kubernetes/frontend/terraform_frontend"** folder and run the commands **"terraform init"**, **"terraform plan"** and **"terraform apply"**.

- In the seventh window, run the command **"minikube tunnel"**.

SSH into the backend pod to run **"python3 manage.py shell"** and apply these commands:
1. **from django.contrib.auth.models import Group, Permission**
2. **new_group, created = Group.objects.get_or_create(name='health_professionals')**
3. **new_group, created = Group.objects.get_or_create(name='investigators')**

Leave the shell and execute the file **"admin_key_iv.py"** to add a key and a iv to the admin to encrypt his information in the database. Exit the pod shell.

Close all windows **except the seventh**.

## App usage

Open your favourite browser and write **localhost** to use the app.
