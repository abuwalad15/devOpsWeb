pipeline {
    agent any
    tools{
        maven 'local_maven'
    }

    stages {
        stage('Build') {
            steps {
                sh 'mvn clean package'
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
                deploy adapters: [tomcat9(credentialsId: 'a68e0dfe-f85c-4b8b-87f0-3aba419695a1', path: '', url: 'http://192.11.15.124:8181/')], contextPath: null, war: '**/*.war'
            }
        }

    }
}
