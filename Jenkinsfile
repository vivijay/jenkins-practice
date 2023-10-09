pipeline {
    agent { node { label 'AGENT-1' } }
    options {
        ansiColor('xterm')
    }
 environment { 
        User = 'vinit'
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
        // stage('Example') {
        //     environment { 
        //         AN_ACCESS_KEY = credentials('my-predefined-secret-text') 
        //     }
        //     steps {
        //         sh 'printenv'
        //     }
        // }
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