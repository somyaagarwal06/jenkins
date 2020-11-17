pipeline {
    agent any
    stages {
        stage('AKS') {
            steps {
	         script {
		    branch = env.GIT_BRANCH
	            echo ${branch}
	          }
          }
        }
        
    }
}
