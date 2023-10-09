pipeline {
    agent { node { label 'AGENT-1' } }
    options {
        ansiColor('xterm')
    }
 environment { 
        cc = 'vinit'
    }
    //  triggers {
    //     cron('* * * * *')
    // }
    stages {
        stage('Build') {
            steps {
                sh'''
                    echo "Building..." 
                    printenv
                '''
            }
        }
        stage('Test') {
            steps {
                sh'''
                    echo "testing"
                '''
            }
        }
        stage('Example') {
            environment { 
                AUTH = credentials('ssh-auth') 
            }
            steps {
                sh 'printenv'
            }
        }
         stage('Input') {
            input {
                message "Should we continue?"
                ok "Yes, we should."
                submitter "alice,bob"
                parameters {
                    string(name: 'PERSON', defaultValue: 'Mr Jenkins', description: 'Who should I say hello to?')
                }
            }
            steps {
                echo "Hello, ${PERSON}, nice to meet you."
            }
        }
    }

    post { 
        always { 
            echo 'I will always run whether job is success or not'
        }
        success{
            echo 'I will run only when job is success'
        }
        failure{
            echo 'I will run when failure'
        }
    }
}