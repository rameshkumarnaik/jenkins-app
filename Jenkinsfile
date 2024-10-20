pipeline {
    agent any

    stages {
        stage('Checkout') {
            steps {
                echo 'Checking out...'
                sh "pwd"
                checkout scm
            }
        }
        stage('Build') {
            steps {
                echo 'Building...'
                sh './gradlew build' // or 'mvn clean install' if using Maven
            }
        }
        stage('Test') {
            steps {
                echo 'Testing...'
                sh './gradlew test' // or 'mvn test' if using Maven
            }
        }
        stage('Deploy') {
            steps {
                echo 'Deploying...'
                //sh 'scp build/libs/your-app.jar user@your-server:/path/to/deploy/' // Adjust as necessary
                //sh 'ssh user@your-server "java -jar /path/to/deploy/your-app.jar &"' // Adjust as necessary
            }
        }
    }

    post {
        always {
            echo 'Cleaning up...'
            archiveArtifacts artifacts: 'build/libs/*.jar', allowEmptyArchive: true
            junit 'build/test-results/test/*.xml' // Adjust if using Maven
        }
    }
}


