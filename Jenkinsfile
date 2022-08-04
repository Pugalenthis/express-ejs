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
            script {
                    sh """
                    #!/bin/bash
                    ssh  -i .ssh/id_rsa ubuntu@13.235.103.64 << EOF
                    touch pugal.html
                    touch jaya.html
                    exit 0
                    << EOF
                    """
                }
            
        }
    }

    }
    
}