pipeline {
  agent none
  stages {
    stage('SCM') {
      agent any
      steps {
        sh 'echo hello'
        sh 'echo $WORKSPACE'
        sh """
        wget https://nodejs.org/dist/v18.18.1/node-v18.18.1-linux-x64.tar.gz
        tar -xvf node-v18.18.1-linux-x64.tar.gz
        """
      }
    }

}
post {
    success {
        println 'WELLDONE'
        //Сохранить артифакты
    }
  }
}
