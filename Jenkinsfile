//jenkins_access_token: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
pipeline {
  agent {
    docker {
      image 'maven:3-alpine'
      args '-v $HOME/.m2:/root/.m2'
    }

  }
  stages {
    stage('Github') {
      steps {
        git(url: 'https://github.com/ariosbpo/cicd-test.git', branch: 'main', changelog: true, credentialsId: 'github')
      }
    }

    stage('Deploy') {
      steps {
	//sh '''pwd'''
        sh '''cd MoquitoProxy/Moquito-v1/
	   mvn install -P test -Dusername=arios@nearbpo.com -Dpassword=K0koniirukar@edg'''
      }
    }

  }
  environment {
    Dev = 'test'
    Prod = 'prod'
  }
}
