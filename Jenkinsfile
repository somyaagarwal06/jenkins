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
				
          }
        }
        
    }
}
