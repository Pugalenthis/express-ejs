pipeline {
    agent any
    parameters {
         string(name: 'express-ejs', defaultValue: '65.0.103.136', description: 'Staging Server')
    }

    triggers {
         pollSCM('* * * * *')
     }

stages{
    stage ("Deploy to Production"){
        steps {
            sh '''
            sudo su
            ssh -i  /home/ubuntu/.ssh/id_rsa ubuntu@${express-ejs}
            cd /var/www/express-ejs
            git pull origin main
            node index.js
            '''
            }
            
        }
    }
}