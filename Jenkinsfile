pipeline {
    agent any

    stages {
	
        stage('CLONE SCM/GITHUM') {		
            steps {
                echo 'cloning from GH'
				git branch: 'main', credentialsId: 'f5ec63fd-36c2-441b-a3b1-132b986eccea', url: 'https://github.com/devopstraininghub/batch10.git'
            }
        }
		
		stage('Build Artifact') {		
            steps {
                echo 'Building using maven'
				sh 'mvn clean install'
            }
        }
		
		stage('TOMCAT DEPLOY') {		
            steps {
                echo 'deploying to tomcat'
				
				deploy adapters: [tomcat9(credentialsId: 'tomcat', path: '', url: 'http://18.206.137.52:8081/')], contextPath: 'facebook', war: '**/*.war'
            }
        }
    }
}
