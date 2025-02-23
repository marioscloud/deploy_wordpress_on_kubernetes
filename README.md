# My Kubernetes Project: Container Orchestration with Kubernetes

## Project Overview
This project provides a comprehensive guide to how to automate the deployment, scaling, and management of containerized applications, showcasing your knowledge in modern container orchestration using Kubernetes. The repository includes a well-structured directory with modular configurations, enabling scalable and maintainable infrastructure as code practices. This repository is ideal for cloud architects, DevOps engineers, and anyone looking to practice Kubernetes skills efficiently.

    • Namespace
    • Secrets
    • Configmap
    • Persistent Volume Claim (PVC)
    • StatefulSet
    • Deployment
    • Services
    • Network Policy.
    
## Prerequisites
- Kubernetes Cluster
- kubectl
- Cluster with admin permission to deploy applications.

## Contact
If you have any questions, feel free to reach out at marioscloud@duck.com.

## Usage
1. Clone the repository:
git clone https://github.com/marioscloud/deploy_wordpress_on_kubernetes

2. Navigate to the directory and initiliaze Git:
git init

3. Create a Namespace:
Run the following commands to create the namespace wordpress and set it as the default.

kubectl create ns wordpress

kubectl config set-context --current --namespace=wordpress\

4. create a secret with a database admin password, username, password, and database name and verify if the secret is created:

kubectl apply -f secret.yaml

kubectl get secret

5. create configmap for Nginx and MySQL, and run the nginx-cm.yaml and mysql-cm.yaml files to create configmap on the WordPress namespace, then confirm that have been created:

kubectl apply -f nginx-cm.yaml

kubectl apply -f mysql-cm.yaml

kubectl get cm

6. create PVC for WordPress and MySQL, then confirm that have been created:

kubectl apply -f pvc.yaml

kubectl get pvc

7. deploy the MySQL database, then confirm that have been done by Kubernetes:

kubectl apply -f mysql.yaml

Then, run the following commands to check if the MySQL StatefulSet and its service is deployed

kubectl get sts

kubectl get svc

For StatefulSet can take for a while to be created, do not worry.

8. Deploy the WordPress application by running the file wordpress.yaml:

kubectl apply -f wordpress.yaml

Now, run the following commands to check if the WordPress deployment and its service is deployed.

kubectl get deploy

kubectl get svc

Then, check the status of PVC and PV using the following commands

kubectl get pvc

kubectl get pv

9. Create a NetworkPolicy for MySQL running the networkpolicy.yaml file and confirm that has been created:

kubectl apply -f networkpolicy.yaml

kubectl get networkpolicy

10. Finally, Log in to WordPress UI:

Once every object has been created, try to access WordPress on the browser by searching on the browser as {node-IP:nodeport}.

You can find the IP address of your node by running the following command: 

kubectl get nodes -o wide

You can find the NodePort assigned to the WordPress service by running: 

kubectl get service wordpress-service -n wordpress

Look for the PORT(S) column in the output, which will show the NodePort. It should look something like 80:30004/TCP, where 30004 is the NodePort.

Thanks for reading.


Acknowledgements
Thanks to the contributors of Nginx configuration and the other for MySQL init script..

Based on exercises contained in the website devopscube published by Aswin Vijayan: https://devopscube.com/deploy-wordpress-on-kubernetes/

