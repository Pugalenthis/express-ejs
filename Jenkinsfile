pipeline {
    agent any
    parameters {
         string(name: 'express-ejs', defaultValue: '13.235.103.64', description: 'Staging Server')
    }

    triggers {
         pollSCM('* * * * *')
     }

stages{
    stage ("PULLING SOURCE CODE"){
        steps {
            script {
                    sh """
                    #!/bin/bash
                    echo ${express-ejs}
                    ssh  -i .ssh/id_rsa ubuntu@${express-ejs} << EOF
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
                    ssh  -i .ssh/id_rsa ubuntu@${express-ejs} << EOF
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
                    ssh  -i .ssh/id_rsa ubuntu@${express-ejs} << EOF
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