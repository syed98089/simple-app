
pipeline {
    agent any
      environment {
            PATH = "/etc/opt/apache-maven-3.8.5/bin:$PATH"
               }
    stages {
        stage('Checkout') {
            steps {
                checkout([$class: 'GitSCM', branches: [[name: '*/master']], extensions: [], userRemoteConfigs: [[credentialsId: 'b732aa57-174c-4bf5-9d38-ac9a31e79960', url: 'https://github.com/syed98089/simple-app.git']]])
            }
        }
      stage('Build') {
            steps {
                       sh  "mvn package"                
            }
        }

    }
}
