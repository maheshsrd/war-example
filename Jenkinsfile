pipeline {
    agent any
    
    tools {
        maven 'm2_home'
    }

    stages {
        stage('git-checkout') {
            steps {
                checkout scmGit(branches: [[name: '*/master']], extensions: [], userRemoteConfigs: [[url: 'https://github.com/maheshsrd/war-example.git']])
            }
        }
        stage('building-source-code') {
            steps {
                sh 'mvn clean package'
            }
        }
        stage('deploy-to-tomcat') {
            steps {
                deploy adapters: [tomcat9(credentialsId: 'tomcat1', path: '', url: 'http://35.180.63.136:8080')], contextPath: '/app', war: '**/*.war'
            }
        }
    }
}



