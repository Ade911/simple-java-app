pipeline {
    agent any

    environment {
        // Define global variables here, if needed (e.g., environment variables, tool versions)
        JAVA_HOME = "/usr/lib/jvm/java-17-openjdk-amd64"
        PATH = "$JAVA_HOME/bin:$PATH"
    }

    stages {
        stage('Build') {
            steps {
                echo 'Building the application...'
                // Commands to build the application (e.g., Maven, Gradle, npm, etc.)
                sh 'mvn clean install'
            }
        }

        stage('Test') {
            steps {
                echo 'Running tests...'
                // Commands to run tests
                sh 'mvn test'
            }
        }

        stage('Deploy') {
            steps {
                echo 'Deploying the application...'
                // Deployment logic (e.g., copying files, pushing to a server, etc.)
                // This could involve SCP, Rsync, or using cloud tools (e.g., AWS CLI).
                sh 'scp target/my-app.jar user@remote-server:/path/to/deploy'
            }
        }
    }

    post {
        always {
            echo 'Pipeline finished.'
        }
        success {
            echo 'Pipeline succeeded!'
        }
        failure {
            echo 'Pipeline failed.'
        }
    }
}
