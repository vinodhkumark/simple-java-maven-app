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
                    echo "PATH = ${PATH}"
                    echo "M2_HOME = ${M2_HOME}"
                    echo "JAVA_HOME = ${JAVA_HOME}"
                    ls ${JAVA_HOME}
                    mvn  -B verify
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
