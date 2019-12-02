pipeline {
    agent any
    tools { 
        maven 'Local_Maven' 
        jdk 'java_home' 
    }
    stages {
        stage ('Initialize') {
            steps {
                sh
                    echo "PATH = ${PATH}"
                    echo "M2_HOME = ${M2_HOME}" 
            }
        }

        stage ('Build') {
            steps {
                echo 'This is a minimal pipeline.'
            }
        }
    }
}