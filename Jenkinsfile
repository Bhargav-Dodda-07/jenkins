pipeline {
    // These are pre-Build sections
    agent {
        node {
            label 'AGENT-1'
        }
    }

    environment {
        COURSE = "jenkins"
    }

     options {
        timeout(time: 10, unit: 'MINUTES')
        disableConcurrentBuilds() 
    }

    parameters {
        string(name: 'PERSON', defaultValue: 'Mr Jenkins', description: 'Who should I say hello to?')
        text(name: 'BIOGRAPHY', defaultValue: '', description: 'Enter some information about the person')
        booleanParam(name: 'TOGGLE', defaultValue: true, description: 'Toggle this value')
        choice(name: 'CHOICE', choices: ['One', 'Two', 'Three'], description: 'Pick something')
        password(name: 'PASSWORD', defaultValue: 'SECRET', description: 'Enter a password')
    }

    stages {
        // This is Build Section
        stage('Build') {
            steps {
                script {
                    sh """
                        echo "Building"
                        echo $COURSE
                        sleep 10
                        env

                        echo "Hello ${params.PERSON}"
                        echo "Biography: ${params.BIOGRAPHY}"
                        echo "Toggle: ${params.TOGGLE}"
                        echo "Choice: ${params.CHOICE}"
                        echo "Password: ${params.PASSWORD}"
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

            // input {
            //      message "Should we continue?"
            //      ok "Yes, we should."
            //      submitter "alice,bob"
            //      parameters {
            //          string(name: 'PERSON', defaultValue: 'Mr Jenkins', description: 'Who should I say hello to?')
            //     }
            // }

            when { 
                expression { "$params.DEPLOY" == "true" }
            }
            
            steps {
                script {
                    sh """
                        echo "Deploying"
                    """
                }
            }
        }
    }

    // These are post-Build sections
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

        aborted {
            echo 'pipeline is aborted'
        }
    }
}