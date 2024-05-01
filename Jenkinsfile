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
                sh 'cp target/Safari.war /home/vboxuser/Documents/DevOps_Software/apache-tomcat-9.0.88/webapps'
            }
        }
        
        stage('slack') {
            steps {
                slackSend baseUrl: 'https://hooks.slack.com/services/', channel: 'notify', color: 'good', message: 'WelCome To Jenkins', notifyCommitters: true, teamDomain: 'MyDevOpsTeam'
            }
        }
    }
}
