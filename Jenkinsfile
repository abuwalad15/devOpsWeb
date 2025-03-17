pipeline {
    agent any
    tools{
        maven 'maven-3.9.9'
    }

    stages {
        stage('Build war file') {
            steps {
                sh 'mvn clean package'
            }
        }

        stage('Deploy to tomcat server') {
            steps {
                    deploy adapters: [tomcat9(credentialsId: 'e03d3314-895c-4135-a5cc-3a4fe4caa3e8', path: '', url: 'http://192.11.15.124:8080/')], contextPath: 'devOpsWeb', war: 'target/*.war'
            }
        }


	stage('Notif'){
		steps{
		emailtext{
			subject: Job Completed,
			body: Jenkins pipeline job completed,
			to: maxwalad@gmail.com
		}
		}
	}

        
    }
}
