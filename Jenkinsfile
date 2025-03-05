pipeline {
    agent any
    tools{
        maven 'maven-3.9.9'
    }

    stages {
        stage('Build') {
            steps {
                sh 'mvn clean install'
            }
            post{
                success{
                    echo "Archiving the Artifacts"
                    archiveArtifacts artifacts: '**/target/*.war'
                }
            }
        }

        stage('Deploy to tomcat server') {
            steps {
                    deploy adapters: [tomcat9(credentialsId: 'a68e0dfe-f85c-4b8b-87f0-3aba419695a1', path: '', url: 'http://54.151.134.78:8080/')], contextPath: null, war: '**/*.war'
            }

        }
    }
}
