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
                deploy adapters: [tomcat9(credentialsId: 'e03d3314-895c-4135-a5cc-3a4fe4caa3e8', path: '', url: 'http://192.11.15.124:8181/')], contextPath: null, war: '**/*.war'
        }

    }
}
