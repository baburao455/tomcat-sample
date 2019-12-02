pipeline {
    agent any
    tools {
        maven 'Local_Maven'
        jdk 'java_home'
    }
    stages {
        stage ('Initialize') {
            steps {
                bat '''
                    echo "PATH = ${PATH}"
                    echo "M2_HOME = ${M2_HOME}"
                '''
            }
        }

        stage ('Build') {
            steps {
                bat 'mvn -Dmaven.test.failure.ignore=true install' 
            }
            post {
                success {
                    junit 'target/surefire-reports/**/*.xml' 
                }
            }
        }
        
        stage('Deploy'){
            steps{
               bat '''
               copy target\tomcat-sample-0.0.1-SNAPSHOT.war C:\server\apache-tomcat-8.5.49\apache-tomcat-8.5.49\webapps
               '''
            }
        }
    }
}