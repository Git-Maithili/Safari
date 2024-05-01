pipeline {
    agent any 
    
    stages {
        stage('Checkout') {
            steps {
                checkout scm
            }
        }
        stage('Build') {
            steps {
                sh '/home/vboxuser/Documents/DevOps_Software/apache-maven-3.9.6/bin/mvn install'
            }
        }
        stage('Deployment') {
            steps {
                sh 'cp target/honda.war /home/vboxuser/Documents/DevOps_Software/apache-tomcat-9.0.88/webapps'
            }
        }
        
        stage('slack') {
            steps {
                slackSend baseUrl: 'https://hooks.slack.com/services/', channel: 'honda', color: 'good', message: 'Welcome to honda in grras with Swapnil Mahajan', notifyCommitters: true, teamDomain: 'DevOps-Grras-Projacts', tokenCredentialId: '91dc5d5d-7361-4216-b88f-d1b1043329c2'
            }
        }
    }
}
