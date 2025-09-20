pipeline{
  agent any

  environment {
    NODE_ENV = 'production'
  }

  stages {
    withEnv(['PATH+NODE=/home/jcast/.nvm/versions/node/v22.19.0/bin']) {
      stage('Build') {
        steps {
          echo 'Building..'
          sh 'npm i -g yarn'
          sh 'yarn'
          sh 'yarn build'
        }
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
