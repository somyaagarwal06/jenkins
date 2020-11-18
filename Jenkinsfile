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
		bat "set branch = ${env.GIT_BRANCH}\naz deployment group create --resource-group Infosys-cloud-cicd --template-file C:\\Resideo\\AKSTemplate\\template.json --parameters C:\\Resideo\\AKSTemplate\\parameters.json --parameters resourceName=INFCLD-%branch:~7%"
         }
        }
        
    }
}
