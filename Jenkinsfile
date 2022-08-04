pipeline {
    agent any
    parameters {
         string(name: 'express-ejs', defaultValue: '13.235.103.64', description: 'Staging Server')
    }

    triggers {
         pollSCM('* * * * *')
     }

stages{
    stage ("Deploy to Production"){
        steps {
            sh "touch index.html"
            }
            
        }
    stage ("DEPLOY CONTAINER"){
        steps {
        
            sh "ssh  -i .ssh/id_rsa ubuntu@13.235.103.64"
            sh "touch pugal.html"
            
        }
    }

    }
    
}