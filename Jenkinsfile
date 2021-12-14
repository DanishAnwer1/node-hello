pipeline {
    agent any; 
environment {
 imageName = "nodehello"
 loc = "/var/lib/jenkins/workspace/github_nodejs_app/node-hello"
 }    
  stages{
        stage('removing previous build') {
            steps {
             sh '''cd /var/lib/jenkins/workspace/github_nodejs_app/
                rm -rf node-hello'''
               }
            }
        stage('copy from-git') {
            steps {
                sh 'git clone https://github.com/DanishAnwer1/node-hello.git'
            }
        }
        stage('Build') {
            steps {
                sh '''cd "${loc}"
                cd "${loc}" npm install'''
            }
        }
        stage('Run as a service') {
           steps {
               sh '''echo "[Service]                                       
ExecStart=/usr/bin/node /var/lib/jenkins/workspace/github_nodejs_app/node-hello/index.js
[Install]
WantedBy=default.target" > /etc/systemd/system/nodejsapp.service
                   systemctl start nodejsapp.service'''
           }
       }
    }
}
