pipeline {
    agent any
    tools {
        // Use the JDK version named "Java 21" configured in Jenkins
        jdk 'Java'
    }

    environment {
        // Defining JAVA_HOME may be optional, depending on your Jenkins configuration
        JAVA_HOME = tool 'Java'
    }
    stages {
        stage('Checkout') {
            steps {
                git url: "https://github.com/spring-projects/spring-petclinic.git" , branch: 'main'
            }
        }
         stage('Build') {
            steps {
                bat '.\\mvnw.cmd clean package'
              }
        }
        stage('Test') {
            steps {
                bat '.\\mvnw.cmd test'
            }    
            post { 
                always { 
                    junit 'target\\surefire-reports\\*.xml' // Publish JUnit test result report
                    }
                }
        }
          
        
    }    
}
