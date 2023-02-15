pipeline {
    agent any

    stages {
        stage('Build') {
            steps {
                sh'''
                 aws ecr get-login-password --region eu-west-2 | docker login --username AWS --password-stdin 700935310038.dkr.ecr.eu-west-2.amazonaws.com
                 docker build -t eli-abukrat-yolo5 .
                 docker tag eli-abukrat-yolo5:latest 700935310038.dkr.ecr.eu-west-2.amazonaws.com/eli-abukrat-yolo5:latest
                 docker push 700935310038.dkr.ecr.eu-west-2.amazonaws.com/eli-abukrat-yolo5:latest

                '''
            }
        }
    }
}

          stage('Trigger Deploy') {
                  steps {
                      build job: '', wait: false, parameters: [
                         string(name: 'YOLO5_IMAGE_URL', value: "<full-url-to-docker-image>")
                         ]
                      }
                   }

          }
 }