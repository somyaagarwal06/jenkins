pipeline {
    agent any
    stages {
        stage('AKS') {
            steps {
                echo "Provisioning AKS Cluster"
                bat """ 
                az account show 
		"""	
		echo env.GIT_BRANCH
		bat "echo "AKS"\nset branch = ${env.GIT_BRANCH}\necho %branch%\necho %branch:~7%"
		bat """
		az deployment group create --resource-group Infosys-cloud-cicd --template-file C:\\Resideo\\AKSTemplate\\template.json --parameters C:\\Resideo\\AKSTemplate\\parameters.json --parameters resourceName=%name%
		"""
          }
        }
        
    }
}
