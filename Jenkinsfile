pipeline {
  agent any
  stages {
    stage('Build Stage ') {
      steps {
        echo 'Building the req for this pipeline'
      }
    }

    stage('Docker stage1') {
      steps {
        sh 'docker ps'
        echo 'Displays the running containers'
      }
    }

  }
}