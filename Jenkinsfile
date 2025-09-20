pipeline{
  agent any

  environment {
    NODE_ENV = 'production'
    NPM_CONFIG_CACHE = "${WORKSPACE}/.npm"
  }

  stages {
    stage('Setup Node.js') {
      steps {
        echo 'Setting up Node.js...'
        sh '''
          export NVM_DIR="$HOME/.nvm"
          nvm install --lts
          node -v
          npm -v
        '''
      }
    }
    stage('Build') {
      steps {
        echo 'Building..'
        withEnv(['PATH+NODE=/home/jcast/.nvm/versions/node/v22.19.0/bin']) {
          sh 'npm install -g yarn'
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
  post {
    always {
        sh '''
          which npm || echo "No npm in PATH"
          which node || echo "No node in PATH"
          which yarn || echo "No yarn in PATH"
          ls -l $(which npm) || true
          whoami
          echo $PATH
        '''
    }
  }
}
