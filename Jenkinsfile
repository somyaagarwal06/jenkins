pipeline {
    agent any
	environment {
	branch = "${env.GIT_BRANCH}"
	}
    stages {
        stage('AKS') {
            steps {
                echo "Provisioning AKS Cluster"
                bat "az account show "
		bat "echo $branch"
		    
		bat "az deployment group create --resource-group Infosys-cloud-cicd --template-file /AKSTemplate/template.json --parameters /AKSTemplate/parameters.json --parameters resourceName=INFCLD-%branch:~7%"
         }
        }
        
    }
}
