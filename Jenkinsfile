
pipeline {
  agent any
  environment {
        TOMCAT_USERNAME = "admin"
        TOMCAT_PASSWORD = "admin"
        TOMCAT_URL = "http://localhost:8080/manager/text"
        TOMCAT_PATH = "/Users/rohanchava/apache-tomcat-9.0.78" // Adjust this to the base directory of your Tomcat installation
  }
  stages {
    stage('Build') {
      steps {
        sh "mvn clean package"
        echo 'Building..'
      }
    }

    stage('Test') {
      steps {
        echo 'Testing..'
      }
    }

    stage('Deploy') {
      steps {
    // Copy the WAR file to the Tomcat webapps directory
    sh "cp ${WORKSPACE}/target/*.war ${TOMCAT_PATH}/webapps/"

     // Stop Tomcat
    sh "cd ${TOMCAT_PATH}/bin && ./shutdown.sh"

    // Start Tomcat
    sh "cd ${TOMCAT_PATH}/bin && ./startup.sh"
        echo 'Deploying....'
      }
    }

  }
}