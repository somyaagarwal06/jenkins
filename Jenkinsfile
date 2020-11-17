pipeline {
    agent any
    parameters{
        choice(name: 'Cluster', choices: ['AKS', 'Minikube'], description: '')
    }
    stages {
	    stage('Checkout SCM') {
            steps {
                checkout([
                 $class: 'GitSCM',
                 branches: [[name: 'main']],
                 userRemoteConfigs: [[
                    url: 'https://github.com/somyaagarwal06/jenkins.git',
                    credentialsId: '',
                 ]]
                ])
            }
        }
        stage('AKS') {
		when {
                expression { params.Cluster == 'AKS' }
            }
            steps {
                echo "Provisioning AKS Cluster"
		echo "Hello"
                bat """ 
                az account show 
		"""
				
          }
        }
        
    }
}
