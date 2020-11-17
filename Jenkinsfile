pipeline {
    agent any
    stages {
        stage('AKS') {
            steps {
                echo "Provisioning AKS Cluster"
                bat "az account show "
		bat "echo ${env.GIT_BRANCH}"
		bat "set branch = ${env.GIT_BRANCH}\naz deployment group create --resource-group Infosys-cloud-cicd --template-file C:\\Resideo\\AKSTemplate\\template.json --parameters C:\\Resideo\\AKSTemplate\\parameters.json --parameters resourceName=%branch:~7%"
         }
        }
        
    }
}
