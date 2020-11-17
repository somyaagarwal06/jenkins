pipeline {
    agent any
    stages {
        stage('AKS') {
            steps {
                echo "Provisioning AKS Cluster"
		echo "Hello jenkins"
                bat """ 
                az account show 
		"""	
		    echo env.GIT_BRANCH
		bat """
		set branch = env.GIT_BRANCH
		set name = %branch:~7%
		az deployment group create --resource-group Infosys-cloud-cicd --template-file C:\\Resideo\\AKSTemplate\\template.json --parameters C:\\Resideo\\AKSTemplate\\parameters.json --parameters resourceName=%name%
		"""
          }
        }
        
    }
}
