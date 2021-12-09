pipeline {
    agent any ; 
     environment {
        JOB_NAME = "github_nodejs_app"
        PATH = "var/lib/jenkins/workspace/github_nodejs_app/node-hello/"
     }
    stages 
    {
        stage('removing previous build') {
            steps {
                sh "rm -rf *"
            }
        }
        stage('copy from-git') {
            steps {
                sh 'git clone https://github.com/DanishAnwer1/node-hello.git'
            }
        }
        //stage('a'){
          //  steps {
               // sh '''cd /var/lib/jenkins/workspace/github_nodejs_app/node-hello
                 //cp *.* /var/lib/jenkins/workspace/github_nodejs_app'''
       //     }
        //}
        stage('Build') {
            steps {
                sh '''cd $PATH
                npm install'''
            }
        }
        stage('Run') {
            steps {
                sh 'npm start'
            }
        }
    }
}
