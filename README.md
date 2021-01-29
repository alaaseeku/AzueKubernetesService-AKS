# AzueKubernetesService-AKS


    LoadBalancer(GloablIP- port 80)
            |
            |
           web                          mysql
Nginx(80) ,PhpImage(9000)           mysql(3306) 
           pod1                          pod2



we use Azure Kubernetes Service (AKS) 

1-	 login to Azure account and create Active Directory service principal account, Run commands
 	az login
 	az ad sp create-for-rbac --skip-assignment

2-	Prepare Kuberentes infrastructure using terraform 
A-	Update terraform file ( terraform.tfvars) 
 	appId    = "jjjjjjjjjjjjjjjj"
 	password = "pppppppppppppppp"
B-	Start building Infrastructure  , Run commands :
 	cd terraform
 	terraform init
 	terraform apply

3-	deploy Kubernetes 

A-	Create Persistent Volume
 	kubectl apply -f Volume.yaml
B-	Create configuration maps
 	kubectl apply -f ConfigMap.yaml
C-	Create secrets 
 	kubectl apply -f secrets.yaml
D-	Create deployment and Service for Mysql
 	kubectl apply -f mysql.yaml
E-	Create deployment and Service for Nginx and php
 	kubectl apply -f Nginx_Php.yaml
