pipeline {
  agent none
  stages {
    stage('SCM') {
      agent any
      steps {
        sh 'echo hello'
        sh 'echo $WORKSPACE'

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
