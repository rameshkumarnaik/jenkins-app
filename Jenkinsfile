pipeline {
    agent any

    environment {
        WORKSPACE_DIR = "${env.WORKSPACE}"
        ARTIFACT_SOURCE = "${WORKSPACE_DIR}/app/build/distributions/app.tar"
        ARTIFACT_DEST = "/mnt/e/repository/backend/artifacts/"
    }
    stages {
        stage('Build') {
            steps {
                echo 'Building...'
                sh 'chmod +x ./gradlew'
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
        stage('Copy Artifacts') {
            steps {
                sh 'cp ${ARTIFACT_SOURCE} ${ARTIFACT_DEST}'
            }
        }
    }

}


