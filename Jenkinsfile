pipeline {
    agent { label 'kubeagent' }
    tools { 
      maven 'MAVEN_HOME' 
      jdk 'JAVA_HOME' 
    }
	stages {
		stage('Checkout') {
			steps {
				script {
					git url: 'https://github.com/piomin/sample-spring-boot-on-kubernetes.git', credentialsId: 'github_credentials'
					sh 'ls -la'
				}
			}
		}
		stage('Build') {
			steps {
				sh 'ls -la'
				sh 'mvn -version'
				sh 'mvn clean compile'
			}
		}
		stage('Test') {
			steps {
				sh 'mvn test'
			}
		}
	}
}
