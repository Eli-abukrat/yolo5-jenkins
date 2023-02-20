pipeline {
    agent any

    stages {
        stage('Unittest') {
            steps {
               sh '''
                pip3 install -r requirements.txt
                python3 -m pytest --junitxml results.xml tests
               '''
            }
            post {
    always {
        junit allowEmptyResults: true, testResults: 'results.xml'
    }
}
        }
        stage('Lint') {
            steps {
                sh '''
                python3 -m pylint *.py
                '''
            }
        }
        stage('Functional test') {
            steps {
                echo "testing"
            }
        }
    }
}