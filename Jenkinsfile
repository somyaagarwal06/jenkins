pipeline {
    agent any
    stages{
       
stage('Deploy') {
      steps {
          dir("C:\\Users\\aksuser\\HELM\\courier-stack\\charts"){
          bat "echo "hello" /n helm list --kubeconfig C:\\Users\\aksuser\\.kube\\config \n\n helm install --generate-name identity --kubeconfig C:\\Users\\aksuser\\.kube\\config \n kubectl get pods --kubeconfig C:\\Users\\aksuser\\.kube\\config"
    }
      }
}
}
}
