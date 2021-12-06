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
        stage('copy fromgit') {
            steps {
                sh 'git clone https://github.com/DanishAnwer1/node-hello.git'
            }
        }
        stage('Build') {
            steps {
                sh 'npm run'
            }
        }
    }
}
