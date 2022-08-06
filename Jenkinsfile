pipeline {
    agent { label 'kubeagent' }
    tools { 
        maven 'maven' 
        jdk 'jdk' 
    }
    environment {
        JAVA_HOME = '/opt/java/openjdk/bin/'
    }
    stages {
        stage ('Initialize') {
            steps {
                withEnv(["JAVA_HOME=/opt/java/openjdk/"]) {
                sh '''
                    mvn clean install package
                ''' 
                }
            }
        }

        stage ('Build') {
            steps {
                echo 'This is a minimal pipeline.'
            }
        }
    }
}
