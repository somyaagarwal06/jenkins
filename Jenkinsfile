pipeline {
    agent any
	environment {
	branch = "${env.GIT_BRANCH}"
	}
    stages {
        stage('AKS') {
            steps {
                echo "Provisioning AKS Cluster"
		echo "Hello S"
                bat "az account show "
		bat "echo $branch"
         }
        }
        
    }
}
