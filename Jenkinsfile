pipeline {
    agent any
    stages {
        stage('SCM') {
            steps {
                echo "Checkout from git"
                sh 'git clone https://github.com/microservices-demo/microservices-demo'
            }
        }
        stage('Build') {
            steps {
                echo 'Building the application...'
                mvn -DskipTests clean install
            }
        }
        stage('Tests') {
            steps {
                echo 'Running unit tests...'
                mvn test
            }
        }
        stage('Deploy') {
      
            steps {
                echo 'Deploying to DEV environment...'
                sh 'kubectl apply -f $WORKSPACE/microservices-demo/manifests/'
            }
        }
    }
}
