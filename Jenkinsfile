pipeline {
    agent any
environment {
    FULL_PATH_BRANCH = "${sh(script:'git name-rev --name-only HEAD', returnStdout: true)}"
    GIT_BRANCH = FULL_PATH_BRANCH.substring(FULL_PATH_BRANCH.lastIndexOf('/') + 1, FULL_PATH_BRANCH.length())
  }
    stages {
	    stage('Checkout SCM') {
            steps {
                checkout([
                 $class: 'GitSCM',
                 branches: [[name: 'main']],
                 userRemoteConfigs: [[
                    url: 'https://github.com/somyaagarwal06/jenkins.git',
                    credentialsId: '',
                 ]]
                ])
            }
        }
        stage('AKS') {
            steps {
echo env.GIT_BRANCH
                echo "Provisioning AKS Cluster"
		echo "Hello"
                bat """ 
                az account show 
		"""
				
          }
        }
        
    }
}
