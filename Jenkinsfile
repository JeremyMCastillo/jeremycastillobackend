pipeline{
  agent any

  environment {
    NODE_ENV = 'production'
    NPM_CONFIG_CACHE = "${WORKSPACE}/.npm"
  }

  stages {
    stage('Build') {
      steps {
        echo 'Copying project files to workspace...'
        sh 'sudo cp -r ./* /var/www/jeremycastillo.net/backend/'
        cd '/var/www/jeremycastillo.net/backend/'

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
        sh 'sudo pm2 restart all'
      }
    }
  }
}
