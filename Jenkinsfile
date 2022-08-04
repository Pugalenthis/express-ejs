pipeline {
    agent any
    triggers {
         pollSCM('* * * * *')
     }

stages{
    stage ("PULLING SOURCE CODE"){
        steps {
            script {
                    sh """
                    #!/bin/bash
                    ssh  -i .ssh/id_rsa ubuntu@13.235.103.64 << EOF
                    cd express-ejs
                    git pull origin main 
                    exit 0
                    << EOF
                    """
                }
            
        }
    }
    stage ("INSTALLING DEPENDENCIES"){
        steps {
            script {
                    sh """
                    #!/bin/bash
                    ssh  -i .ssh/id_rsa ubuntu@13.235.103.64 << EOF
                    cd express-ejs
                    npm install
                    exit 0
                    << EOF
                    """
                }
            
        }
    }
    stage ("RUNNING AN APPLICATION"){
        steps {
            script {
                    sh """
                    #!/bin/bash
                    ssh  -i .ssh/id_rsa ubuntu@13.235.103.64 << EOF
                    lsof -t -i:8080 | xargs kill -9
                    cd express-ejs 
                    node index.js
                    exit 0
                    << EOF
                    """
                }
            
        }
    }

    }
    
}