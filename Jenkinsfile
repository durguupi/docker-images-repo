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

    stage('Changing directory') {
      steps {
        dir(path: 'nodejsapp') {
          sh '''pwd
ls -ltrh'''
        }

      }
    }

    stage('NPM install Stage') {
      steps {
        dir(path: 'nodejsapp') {
          sh '''npm install
ls -ltrh
'''
          echo 'Successfully installed npm packages and locks'
        }

      }
    }

    stage('Docker build') {
      steps {
        dir(path: 'nodejsapp') {
          sh 'docker build -t local/node-web-app .'
          sh '''echo "Listing of docker images"
docker images'''
        }

      }
    }

    stage('Docker run') {
      steps {
        dir(path: 'nodejsapp') {
          echo 'Running docker image'
          sh 'docker run -p 49160:8080 -d local/node-web-app'
        }

        sh '''echo "Display the running container"
docker ps'''
      }
    }

    stage('Display Stage') {
      steps {
        ansiColor(colorMapName: 'xterm') {
          sh 'curl -i localhost:49160'
          echo 'Displays the local page output of nodejs app'
        }

      }
    }

  }
}