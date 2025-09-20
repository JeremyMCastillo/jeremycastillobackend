pipeline{
  agent any

  environment {
    NODE_ENV = 'production'
  }

  stages {
    stage('Build') {
      steps {
        echo 'Building..'
        sh 'yarn'
        yarn
        yarn command: 'build'
      }
    }
    stage('Deploy') {
      steps {
        echo 'Deploying....'
        sh 'cp -r ./* /var/www/jeremycastillo.com/backend/'
        sh 'pm2 restart all'
      }
    }
  }
}
