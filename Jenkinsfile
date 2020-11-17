pipeline {
    agent any
    stages {
        stage('AKS') {
            steps {
                echo "Provisioning AKS Cluster"
		echo "Hello update"
                bat """ 
                az account show 
		"""	
		    echo ${env.BRANCH_NAME}
          }
        }
        
    }
}
