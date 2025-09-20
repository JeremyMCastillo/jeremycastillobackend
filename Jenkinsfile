pipeline{
  agent any
  stages {
    stage('Build') {
      steps {
        echo 'Building..'
        sh 'yarn'
        sh 'NODE_ENV=production yarn build'
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
