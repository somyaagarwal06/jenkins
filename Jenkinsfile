pipeline {
    agent any
    stages {
        stage('AKS') {
            steps {
                echo "Provisioning AKS Cluster"
		echo "Hello"
                bat """ 
                az account show 
		"""	
		    echo env.GIT_BRANCH
          }
        }
        
    }
}
