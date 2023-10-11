pipeline {
  agent none
  parameters {
		 string(
			name: 'BRANCH',
			defaultValue: 'main',
			description: 'BRANCH'
		)


    }
  stages {
    stage('SCM') {
      agent any
      steps {
        script {
        sh 'echo hello'
        sh 'echo $WORKSPACE'
        sh """
        wget https://nodejs.org/download/release/v17.9.1/node-v17.9.1-linux-x64.tar.gz
        tar -xvf node-v17.9.1-linux-x64.tar.gz
        """
        CODE_REPO='git@github.com:RoboInterativo/robo-docs.git'
        checkout([$class: 'GitSCM', branches: [[name: BRANCH]],
               doGenerateSubmoduleConfigurations: false,
               extensions: [[$class: 'RelativeTargetDirectory',
               relativeTargetDir: 'app/']], gitTool: 'Default',
               submoduleCfg: [], userRemoteConfigs: [[credentialsId: 'ssh-git',
               url: CODE_REPO]]])

        nodejs="$WORKSPACE/node-v17.9.1-linux-x64/bin"

        sh """
        export PATH="$nodejs:$PATH"
        node --version
        cd app/my-website2
        npm install
        npm run build
        """
      }
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
