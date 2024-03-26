pipeline {
    agent any
    tools {
        maven 'mymaven'
    }
   environment {
        TOMCAT_MANAGER_USERNAME = 'manager' // Tomcat Manager username
        TOMCAT_MANAGER_PASSWORD = 'manager' // Tomcat Manager password
        TOMCAT_HOST = 'localhost' // Tomcat host
        TOMCAT_PORT = '8082' // Tomcat port
        WAR_FILE_PATH = '/var/lib/jenkins/workspace/my-pipeline/target/addressbook-2.0.war' // Path to your WAR file
        CONTEXT_PATH = null // Context path where you want to deploy your application
    }
    stages {
        stage('Fetching Code from Git') {
            steps {
                git branch: 'master', url: 'https://github.com/Dhruvakumarkr/addressbook.git'
            }
        }
        stage('Compile the code') {
            steps {
                sh 'mvn compile'
            }
        }
        stage('Testing the code') {
            steps {
                sh 'mvn test'
            }
        }
      stage('Packaging the code') {
            steps {
                sh 'mvn package'
            }
        }
      stage('Deploy WAR file') {
            steps {
                script {
                    // Use curl to deploy the WAR file to Tomcat Manager
                    sh "curl -v -u ${TOMCAT_MANAGER_USERNAME}:${TOMCAT_MANAGER_PASSWORD} --upload-file ${WAR_FILE_PATH} http://${TOMCAT_HOST}:${TOMCAT_PORT}/manager/text/deploy?path=/${CONTEXT_PATH}"
                }
            }
        } 

        
    }

    
}
