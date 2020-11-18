pipeline {
    agent any
	environment {
	branch = "${env.GIT_BRANCH}"
	}
    stages {
        stage('AKS') {
            steps {
                echo "Provisioning AKS Cluster"
		echo "demo branch"
                bat "az account show "
		bat "az deployment group create --resource-group Infosys-cloud-cicd --template-file AKSTemplate/template.json --parameters AKSTemplate/parameters.json --parameters resourceName=INFCLD-%branch:~7%"
                bat "az aks get-credentials --resource-group Infosys-cloud-cicd --name INFCLD-%branch:~7%"	
		bat """ 
		cd C:\\Resideo\\Services\\skaffold\\managementapi\\templates
		kubectl apply -f secrets.yaml
		kubectl create secret docker-registry resideohelmkey --docker-server=greenqaacr.azurecr.io --docker-username=greenqaacr --docker-password=NjiFKy5v00vWyNkWpVQmE7zHicBKG/8B
		skaffold run
		helm list
		kubectl get pods 
		""" 
		bat '''
		cd C:\\Resideo\\Services
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
        
    }
}
