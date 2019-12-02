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
               JENKINS_JOB_WS='/var/lib/jenkins/jobs/dev/workspace'
               CATALINA_HOME='/usr/share/apache-tomcat-8.0.23'
               WEB_APPS_DIR=$CATALINA_HOME'/webapps'
               WEB_APP=$WEB_APPS_DIR'/fre'
               echo JENKINS_JOB_WS
               '''
            }
        }
    }
}