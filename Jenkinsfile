pipeline {
    agent any
    parameters {
         string(name: 'express-ejs', defaultValue: '65.0.103.136', description: 'Staging Server')
    }

    triggers {
         pollSCM('* * * * *')
     }

stages{

        stage ('Deployments'){
                stage ("Deploy to Production"){
                    steps {
                        sh '''
                        ssh -i  /home/ubuntu/.ssh/id_rsa.pub ubuntu@${express-ejs}
                        cd /var/www/express-ejs
                        git pull origin main
                        node index.js
                        '''
                    }
                }
            
        }
    }
}