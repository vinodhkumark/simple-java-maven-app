pipeline {
  agent {
    kubernetes {
      yaml '''
        apiVersion: v1
        kind: Pod
        spec:
          containers:
          - name: maven
            image: maven:alpine
            command:
            - cat
            tty: true
          - name: docker
            image: docker:latest
            command:
            - cat
            tty: true
            volumeMounts:
             - mountPath: /var/run/docker.sock
               name: docker-sock
          - name: kaniko
            image: gcr.io/kaniko-project/executor:debug
            command:
            - sleep
            args:
            - 9999999
            volumeMounts:
            - name: kaniko-secret
              mountPath: /kaniko/.docker
          volumes:
          - name: docker-sock
            hostPath:
              path: /var/run/docker.sock
          - name: kaniko-secret
            secret:
              secretName: saas-credentials
              items:
                - key: .dockerconfigjson
                  path: config.json
        '''
    }
  }
  stages {
    stage('Clone') {
      steps {
        container('maven') {
          git branch: 'main', changelog: false, poll: false, url: 'https://mohdsabir-cloudside@bitbucket.org/mohdsabir-cloudside/java-app.git'
        }
      }
    }  
    stage('Build-Jar-file') {
      steps {
        container('maven') {
          sh 'mvn package'
        }
      }
    }
    stage ('Exec Kaniko') {
      steps { 
        container('kaniko') {
          sh '''
            cat /kaniko/.docker/config.json
            /kaniko/executor --context `pwd` --destination vinodhkumark1:/javaapp:1.0
            '''
        }
      }
    }
  }
}
