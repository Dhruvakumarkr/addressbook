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
        stage('Packaging the code') {
            steps {
                sh 'mvn package'
            }
        }

    }
}
