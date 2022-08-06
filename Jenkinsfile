pipeline {
    agent { label 'kubeagent' }
    tools { 
        maven 'maven' 
        jdk 'jdk' 
    }
    stages {
        stage ('Initialize') {
            steps {
                sh '''
                    echo "PATH = ${PATH}"
                    echo "M2_HOME = ${M2_HOME}"
                    echo "JAVA_HOME = ${JAVA_HOME}"
                    export JAVA_HOME = /opt/java/openjdk/bin
                    mvn  -B verify
                ''' 
            }
        }

        stage ('Build') {
            steps {
                echo 'This is a minimal pipeline.'
            }
        }
    }
}
