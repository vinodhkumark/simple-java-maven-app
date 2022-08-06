pipeline {
    agent { label 'kubeagent' }
  stages {
    stage('Maven Install') {
      agent {
        docker {
          label 'kubeagent'
          image 'maven:3.8.6-jdk-8'
        }
      }
      steps {
        sh 'mvn clean install'
      }
    
    }
  }
}
