pipeline {
    agent any
    stages {
        stage('AKS') {
            steps {
		    script{
		    branch= ${env.GIT_BRANCH}
		    echo %branch%
		    }
                echo "Provisioning AKS Cluster"
                bat """ 
                az account show 
		"""	
		    echo env.GIT_BRANCH
		bat """
		echo "AKS"
		set branch = ${env.GIT_BRANCH}
		echo %branch%
		echo %branch:~7%
		az deployment group create --resource-group Infosys-cloud-cicd --template-file C:\\Resideo\\AKSTemplate\\template.json --parameters C:\\Resideo\\AKSTemplate\\parameters.json --parameters resourceName=%name%
		"""
          }
        }
        
    }
}
