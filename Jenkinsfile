pipeline {
    agent any
    parameters {
         string(name: 'express-ejs', defaultValue: '13.235.103.64', description: 'Staging Server')
    }

    triggers {
         pollSCM('* * * * *')
     }

stages{
    stage ("DEPLOY TO PRODUCTION"){
        steps {
            script {
                    sh """
                    #!/bin/bash
                    ssh  -i .ssh/id_rsa ubuntu@${express-ejs} << EOF
                    cd express-ejs
                    git pull origin main 
                    node index.js
                    exit 0
                    << EOF
                    """
                }
            
        }
    }

    }
    
}