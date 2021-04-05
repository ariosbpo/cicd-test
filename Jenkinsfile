//jenkins_access_token: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
pipeline {
  agent {
    docker {
      image 'maven:3-alpine'
      args '-v /root/.m2:/root/.m2'
    }

  }
  stages {
    stage('Github') {
      steps {
        git(url: 'https://github.com/AlanMalagon/apigee-cicd-test.git', branch: 'main', changelog: true, credentialsId: 'github')
      }
    }

    stage('Deploy') {
      steps {
        sh '''cd src/gateway/test-app/
mvn install -P test -Dusername=arios@nearbpo.com -Dpassword=K0koniirukar@bpo'''
      }
    }

  }
  environment {
    Dev = 'test'
    Prod = 'prod'
  }
}
