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
                rm -rf node-hello'''
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
            //    cd "${loc}" npm install'''
            }
        }
        stage('Build') {
           steps {
               sh '''cd "${cloc}" npm install'''
                // 'pm2 start index.js'
           }
       }
      stage('Deployment') {
          steps { 
              sh '"${cloc} pm2 start index.js"'
         //     'pm2 start index.js'''
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
