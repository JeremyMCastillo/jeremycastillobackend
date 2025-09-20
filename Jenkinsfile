pipeline{
  agent any

  environment {
    NODE_ENV = 'production'
  }

  stages {
    stage('Build') {
      steps {
        echo 'Building..'
        withEnv(['PATH+NODE=/home/jcast/.nvm/versions/node/v22.19.0/bin']) {
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
