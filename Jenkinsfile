pipeline {
  agent any
  stages {
    stage('Git Checkout') {
      steps {
        git(url: 'https://github.com/adamzhanovt/my-cicd-pipeline', branch: 'main')
      }
    }

    stage('Application Build') {
      steps {
        sh 'script scripts/build.sh'
      }
    }

    stage('Tests') {
      steps {
        sh 'script scripts/test.sh'
      }
    }

    stage('Docker Image Build') {
      steps {
        sh 'docker build -t mydockerimage .'
      }
    }

    stage('Docker Image Push') {
      steps {
        sh '''docker login -u "adamzhanovt" -p "Evhf2013!"  https://index.docker.io/v1/
docker push adamzhanovt/myfirstrepo:latest'''
      }
    }

  }
}