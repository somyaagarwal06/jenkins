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
          }
        }
        
    }
}
