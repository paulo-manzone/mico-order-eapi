pipeline {
    agent any
    options {
    	ansiColor('xterm')  
  	}
    environment {
    	AP_CLIENT_ID = credentials('ap.client_id')
    	AP_CLIENT_SECRET = credentials('ap.client_secret')
    }
    stages {
        stage('Build') {
        	steps {
                bat 'mvn clean install'
            }
        }
        stage('Deploy to CloudHub') {
        	steps {
                bat 'mvn mule:deploy -DmuleDeploy -Dmule.artifact=./target/mico-order-eapi-1.0.11-mule-application.jar -Dap.client_id=${AP_CLIENT_ID} -Dap.client_secret=${AP_CLIENT_SECRET}'
            }	
        }
   	}
