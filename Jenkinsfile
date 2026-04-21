pipeline {
    agent {
        node {
            label 'AGENT-1'
        }
    }

    environment {
        COURSE = "jenkins"
    }

     options {
        timeout(time: 10, unit: 'SEC') 
    }

    stages {
        stage('Build') {
            steps {
                script {
                    sh """
                        echo "Building"
                        echo $COURSE
                        sleep 10
                        env
                    """
                }
            }
        }
        stage('Test') {
            steps {
                script {
                    sh """
                        echo "Testing"
                    """
                }
            }
        }
        stage('Deploy') {
            steps {
                script {
                    sh """
                        echo "Deploying"
                    """
                }
            }
        }
    }

    post {
        always {
            echo 'I will always say Hello again!'
            cleanWs()
        }

        success {
            echo 'I will run if succeeded'
        }

        failure {
            echo 'I will run if fails'
        }
    }
}