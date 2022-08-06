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
                    ls /home/jenkins/agent/tools/hudson.tasks.Maven_MavenInstallation/maven/bin/
                    /home/jenkins/agent/tools/hudson.tasks.Maven_MavenInstallation/maven/bin/mvn  -B verify
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
