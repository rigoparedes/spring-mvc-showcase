pipeline {
  agent any
  /*
  tools {
        // maven 'maven-3.3.9'
        // jdk 'jdk8'
  }
  */
  stages {

    stage('Checkout') {
	  steps {
		checkout scm
	  }
	}

    stage ('Build') {
      steps {
        sh 'mvn -Dmaven.test.failure.ignore=true package' 
      }
      post {
        success {
          junit 'target/surefire-reports/**/*.xml' 
        }
      }
    }        
        
    stage ('Deploy') {
      steps {
        sh '''
          cp target/spring-mvc-showcase.war /opt/wildfly2/standalone/deployments/
        '''
        }
      }
    }
}
