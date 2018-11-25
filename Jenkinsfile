pipeline {

  environment {
    registry = "chanchal/jenkinsbuild"
    registryCredential = 'dockerhub'
  }

  agent any

  stages {
    stage('Cloning Git') {
      steps {
        git 'https://github.com/chanchalbose/hellonode.git'
      }
    }
    stage('Building image') {
      steps{
        script {
          dockerImage = docker.build registry + ":$BUILD_NUMBER"
        }
      }
    }
    stage('Deploy Image') {
      steps{
        script {
          docker.withRegistry( '', registryCredential ) {
            dockerImage.push()
          }
        }
      }
    }
  }
}
