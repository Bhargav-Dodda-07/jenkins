pipeline {
    agent {
        node {
            label 'AGENT-1'
        }
    } 
    stages {
        stage('Build') { 
            steps {
                echo "buliding"
            }
        }
        stage('Test') { 
            steps {
                echo "Testing"
            }
        }
        stage('Deploy') { 
            steps {
                echo "Deploying" 
            }
        }
    }
}