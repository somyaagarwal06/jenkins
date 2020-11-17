pipeline {
    agent any
    stages {
        stage('AKS') {
            steps {
                echo "Provisioning AKS Cluster"
                bat "az account show "
		bat "echo ${env.GIT_BRANCH}"
		    bat "set branch = ${env.GIT_BRANCH}\n echo {branch}"
         }
        }
        
    }
}
