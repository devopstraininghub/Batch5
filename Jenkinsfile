pipeline {
    agent any

    stages {
        stage('clone SCM stage ') {
            steps {
                echo 'cloning game of life source code'
				git 'https://github.com/wakaleo/game-of-life.git'
            }
        }
		
		stage('building .war artifact from sourcecode  ') {
            steps {
                echo 'maven artifact building'
				sh 'mvn clean install'
            }
        }
		
		stage('Deploy to Tomcat application server') {
            steps {
                echo 'Deploy to Tomcat application server'
				deploy adapters: [tomcat9(credentialsId: 'ae23c13f-e9b6-4e70-b365-6ed3a039ee55', path: '', url: 'http://13.127.210.51:8080/')], contextPath: 'batch5', war: '**/*.war'
            }
        }
		
    }
}
