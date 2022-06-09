
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

	 stage('Nexus-artifact Upload') {
            steps {
                       nexusArtifactUploader artifacts: [[artifactId: 'maven-project', classifier: '', file: '/var/lib/jenkins/workspace/build_job/webapp/target/webapp.war', type: 'war']], credentialsId: 'nexus_33', groupId: 'com.example.maven-project', nexusUrl: '172.31.90.105:8081', nexusVersion: 'nexus3', protocol: 'http', repository: 'simple-app', version: '1.0.0'            }
        }         



    }
}
