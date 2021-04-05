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
        git(url: 'https://github.com/ariosbpo/apigee-cicd-test.git', branch: 'main', changelog: true, credentialsId: 'github')
      }
    }

    stage('Deploy') {
      steps {
        sh '''cd $HOME/workspace/apigee_projects/cicd-test
mvn install -P test -Dusername=arios@nearbpo.com -Dpassword=K0koniirukar@bpo'''
      }
    }

  }
  environment {
    Dev = 'test'
    Prod = 'prod'
  }
}
