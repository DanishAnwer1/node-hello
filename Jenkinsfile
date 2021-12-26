pipeline {
    agent any; 
environment {
 imageName = "nodehello"
 loc = "/var/lib/jenkins/workspace/github_nodejs_app/node-hello"
 locc = "/var/lib/jenkins/workspace/github_nodejs_app/"
 cloc = "/opt/nodejs"
    }    
  stages{
        stage('removing previous build') {
            steps {
              sh '''cd "${locc}"
                rm -rf node-hello
                pm2 delete index.js'''
               }
            }
        stage('Code check out') {
            steps {
                sh 'git clone https://github.com/DanishAnwer1/node-hello.git'
            }
        }
        stage('Copying to opt') {
            steps {
                sh '''cd "${loc}"
                cp *.* "${cloc}"'''
            }
        }
        stage('Build') {
           steps {
               sh '''cd "${cloc}" 
               npm install'''
           }
       }
      stage('Deployment') {
          steps { 
              sh '''cd "${cloc}" 
              pm2 start index.js'''
          }
      }
//     stage('Check error code') {
//             steps {
//                 sh '''if [ $? -eq 0 ]
//                           then
//                           echo "The script ran ok"
//                           exit 0
//                           else
//                           echo "The script failed" >&2
//                           exit 1
//                           fi'''
//             }
//         }
    }
}
