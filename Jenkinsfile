pipeline {
    agent 
     {
      label 'Springboot-Microservices'
        }



    stages {
        stage('Checkout') {
            steps {
                // Pull code from Git
                git branch: 'main', url: 'https://github.com/priyaranjansila-a11y/maven-project-priya.git'
            }
        }

        stage('Build') {
            steps {
                // Run Maven build
                sh 'mvn clean install'
            }
        }

        stage('Package') {
            steps {
                // Create JAR file
                sh 'mvn package'
            }
            post {
                success {
                    archiveArtifacts artifacts: 'target/*.jar', fingerprint: true
                }
            }
        }
    }

    post {
        always {
            echo 'Pipeline execution finished.'
        }
    }
}
