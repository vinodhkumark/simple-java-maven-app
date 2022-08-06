pipeline {
    agent { label 'kubeagent' }
  stages {
    stage('Maven Install') {
      agent {
        docker {
          label 'kubeagent'
          image 'maven:3.5.0'
        }
      }
      steps {
        sh 'mvn clean install'
      }
    
    }
  }
}
