pipeline {
    agent any

    stages 
    {
        stage('removing previous build') {
            steps {
                sh '''cd /var/lib/jenkins/workspace/github_nodejs_app/ 
                    rm -rf *'''
            }
        }
        stage('copy from-git') {
            steps {
                sh 'git clone https://github.com/DanishAnwer1/node-hello.git'
            }
        }
        stage('assinging rights'){
            steps {
                sh 'chmod -R 777 /var/lib/jenkins/workspace/github_nodejs_app'
            }
        }
        stage('Build') {
            steps {
                sh 'npm build'
            }
        }
        stage('Run') {
            steps {
                sh 'npm run'
            }
        }
    }
}
