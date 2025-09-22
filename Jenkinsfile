pipeline{
  agent any

  environment {
    NODE_ENV = 'production'
    NPM_CONFIG_CACHE = "${WORKSPACE}/.npm"
  }

  stages {
    stage('Build') {
      steps {
        echo 'Building..'
        nvm('22.19.0') {
          sh 'npm install -g yarn'
          sh 'yarn'
          sh 'yarn build'
        }
      }
    }
    stage('Deploy') {
      steps {
        echo 'Deploying....'
        sh 'sudo cp -r ./* /var/www/jeremycastillo.net/backend/'
        sh 'sudo pm2 restart all'
      }
    }
  }
}
