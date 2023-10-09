pipeline {
    agent { node { label 'AGENT-1' } }
    options {
        ansiColor('xterm')
    }
 environment { 
        cc = 'vinit'
    }
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