pipeline {
    agent any
    tools {
        maven 'mymaven'
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
    }
    post {
   	 always {
   	 step([$class: 'JacocoPublisher',
   	   	execPattern: 'target/*.exec',
   	   	classPattern: 'target/classes',
   	   	sourcePattern: 'src/main/java',
   	   	exclusionPattern: 'src/test*'
   	 ])
   	 }   
    	}

}
