pipeline {
  agent any
  tools {
    maven 'Maven3' 
  }
  stages {
      stage ('sravan Build Code') {
      steps {
        sh 'mvn clean package'
      }
    }
    stage ('Deploy') {
      steps {
        script {
          deploy adapters: [tomcat9(credentialsId: 'tomcat-deployer-key', path: '', url: 'http://localhost:8080')], contextPath: '/helloWorld', onFailure: false, war: 'webapp/target/*.war' 
        }
      }
    }
  }
}
