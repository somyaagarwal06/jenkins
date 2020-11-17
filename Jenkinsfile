pipeline {
    agent any
    parameters{
        choice(name: 'Cluster', choices: ['AKS', 'Minikube'], description: '')
    }
    stages {
        stage('AKS') {
		when {
                expression { params.Cluster == 'AKS' }
            }
            steps {
                echo "Provisioning AKS Cluster"
                bat """ 
                az account show 
				"""
				bat """ 
				az deployment group create --resource-group Infosys-cloud-cicd --template-file C:\\Resideo\\AKSTemplate\\template.json --parameters C:\\Resideo\\AKSTemplate\\parameters.json
				"""
				bat """ 
				az aks get-credentials --resource-group Infosys-cloud-cicd --name INFCLD-AKS-04
				"""	
			/**	bat """ 
				az acr login -n greenqaacr -u greenqaacr --password NjiFKy5v00vWyNkWpVQmE7zHicBKG/8B 
				""" **/
				bat """ 
				cd C:\\Resideo\\Services\\mssql
				kubectl create secret docker-registry resideohelmkey --docker-server=greenqaacr.azurecr.io --docker-username=greenqaacr --docker-password=NjiFKy5v00vWyNkWpVQmE7zHicBKG/8B
				skaffold run
				helm list
				kubectl get pods 
				""" 
				bat '''
				cd C:\\Resideo\\Services
				kubectl create secret generic rabbitmq --from-literal=QUEUEPASSWORD=pass@123456 --from-literal=QUEUEUSERNAME=user@1234 --from-literal=rabbitmq-erlang-cookie=uSer@1234 --from-literal=rabbitmq-password=pAss@1234
				helm install rabbitmq rabbitmq
				kubectl get pods
				'''
				bat'''
				cd C:\\Resideo\\Services
				kubectl create secret generic redis --from-literal=redis-password=**anything
				helm install redis redis
				kubectl get pods
				'''
				bat'''
				cd C:\\Resideo\\Services
				kubectl create secret generic kafka --from-literal=KAFKASASLUSERNAME=kafkauser@1234 --from-literal=KAFKASASLPASSWORD=pass@1234
				helm install kafka kafka
				kubectl get pods
				'''
				bat'''
				cd C:\\Resideo\\Services
				kubectl create secret generic identity
				helm install identity identity
				kubectl get pods
				'''
				bat'''
				cd C:\\Resideo\\Services
				kubectl create secret generic managementapi
				helm install managementapi managementapi
				kubectl get pods
				'''
				bat'''
				cd C:\\Resideo\\Services
				kubectl create secret generic api
				helm install courierapi courierapi
				kubectl get pods
				'''
				bat'''
				cd C:\\Resideo\\Services
				kubectl create secret generic forwardingservice --from-literal=CLIENTID=client@1234 --from-literal=CLIENTSECRET=secret@7654
				helm install forwardingservice forwardingservice
				kubectl get pods
				'''
				bat'''
				cd C:\\Resideo\\Services
				helm install router router
				kubectl get pods
				'''
          }
        }
        stage('Minikube'){
          when {
                expression { params.Cluster == 'Minikube' }
            }
            steps {
                echo "Provisioning Minikube cluster"
                bat '''
                Choco install minikube
				minikube config set memory 4000
				minikube config set driver docker
				minikube delete
				minikube start'''
				bat '''
				az acr login -n greenqaacr -u greenqaacr --password NjiFKy5v00vWyNkWpVQmE7zHicBKG/8B
				'''
				bat '''
				cd C:\\Resideo\\Services\\mssql
				kubectl config use-context minikube
				kubectl create secret docker-registry resideohelmkey --docker-server=greenqaacr.azurecr.io --docker-username=greenqaacr --docker-password=NjiFKy5v00vWyNkWpVQmE7zHicBKG/8B
				skaffold run
				helm list
				kubectl get pods
				'''
				bat '''
				cd C:\\Resideo\\Services
				kubectl config use-context minikube
				kubectl create secret generic rabbitmq --from-literal=QUEUEPASSWORD=pass@123456 --from-literal=QUEUEUSERNAME=user@1234 --from-literal=rabbitmq-erlang-cookie=uSer@1234 --from-literal=rabbitmq-password=pAss@1234
				helm install rabbitmq rabbitmq
				kubectl get pods
				'''
				bat'''
				cd C:\\Resideo\\Services
				kubectl config use-context minikube
				kubectl create secret generic redis --from-literal=redis-password=**anything
				helm install redis redis
				kubectl get pods
				'''
				bat'''
				cd C:\\Resideo\\Services
				kubectl config use-context minikube
				kubectl create secret generic kafka --from-literal=KAFKASASLUSERNAME=kafkauser@1234 --from-literal=KAFKASASLPASSWORD=pass@1234
				helm install kafka kafka
				kubectl get pods
				'''
				bat'''
				cd C:\\Resideo\\Services
				kubectl config use-context minikube
				kubectl create secret generic identity
				helm install identity identity
				kubectl get pods
				'''
				bat'''
				cd C:\\Resideo\\Services
				kubectl config use-context minikube
				kubectl create secret generic managementapi
				helm install managementapi managementapi
				kubectl get pods
				'''
				bat'''
				cd C:\\Resideo\\Services
				kubectl config use-context minikube
				kubectl create secret generic api
				helm install courierapi courierapi
				kubectl get pods
				'''
				bat'''
				cd C:\\Resideo\\Services
				kubectl config use-context minikube
				kubectl create secret generic forwardingservice --from-literal=CLIENTID=client@1234 --from-literal=CLIENTSECRET=secret@7654
				helm install forwardingservice forwardingservice
				kubectl get pods
				'''
				bat'''
				cd C:\\Resideo\\Services
				kubectl config use-context minikube
				helm install router router
				kubectl get pods
				'''
          }     
    }
    }
}
