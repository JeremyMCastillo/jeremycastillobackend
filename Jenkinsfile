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
        withEnv(['PATH+NODE=/home/jcast/.nvm/versions/node/v22.19.0/bin']) {
          sh 'npx yarn'
          sh 'npx yarn build'
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
