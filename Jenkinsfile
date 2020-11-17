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
		bat """
		echo "AKS"
		set branch = ${env.GIT_BRANCH}
		for /f "tokens=2 delims=//" %%a in ("%branch%") do (
  set name=%%a
)
		echo %name%
		az deployment group create --resource-group Infosys-cloud-cicd --template-file C:\\Resideo\\AKSTemplate\\template.json --parameters C:\\Resideo\\AKSTemplate\\parameters.json --parameters resourceName=%name%
		"""
          }
        }
        
    }
}
