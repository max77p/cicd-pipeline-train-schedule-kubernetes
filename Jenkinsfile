//sdfafasfds
pipeline {
    agent any
    environment {
        //be sure to replace "willbla" with your own Docker Hub username
        DOCKER_IMAGE_NAME = "shancode1103/train-schedule"
    }
          parameters {
          booleanParam (name: 'BUILD_UI_APP', defaultValue: false, description: 'Build UI?')
          //booleanParam (name: 'BUILD_UI_MOCK_APP', defaultValue: false, description: 'Build UI Mock?')
          booleanParam (name: 'BUILD_BACKEND_APP', defaultValue: false, description: 'Build Backend?')
          booleanParam (name: 'BUILD_BACKEND_MOCK_APP', defaultValue: false, description: 'Build Backend Mock?')
      }
    stages {
        stage('Build') {
            steps {
                echo 'Running build automation'
                sh './gradlew build --no-daemon'
                archiveArtifacts artifacts: 'dist/trainSchedule.zip'
            }
        }
        stage('Build Docker Image') {
            agent { dockerfile true }
                steps {
                sh 'node --version'
            }
        }
    }
}
