pipeline {
    agent any

    environment {
        IMAGE_NAME = "devops-project"
        CONTAINER_NAME = "devops-app"
        PORT = "80"
    }

    stages {

        stage('Build') {
            steps {
                echo 'Building the application...'
                // If you have a Node.js app or Java app, build commands go here
                // e.g., sh 'npm install' or sh 'mvn clean install'
            }
        }

        stage('Docker Build') {
            steps {
                echo 'Building Docker image...'
                sh "docker build -t $IMAGE_NAME ."
            }
        }

        stage('Docker Deploy') {
            steps {
                echo 'Deploying Docker container...'
                // Stop & remove any existing container
                sh "docker stop $CONTAINER_NAME || true"
                sh "docker rm $CONTAINER_NAME || true"
                // Run the container
                sh "docker run -d --name $CONTAINER_NAME -p $PORT:$PORT $IMAGE_NAME"
            }
        }

    }

    post {
        success {
            echo 'Pipeline completed successfully!'
        }
        failure 
        {
            echo 'Pipeline failed!'
        }
    }
}
