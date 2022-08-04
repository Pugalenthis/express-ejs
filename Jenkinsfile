pipeline {
    agent any
    parameters { 
         string(name: 'IP_ADDRESS', defaultValue: '35.166.210.154', description: 'Staging Server')
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
                    ssh  -i .ssh/id_rsa ubuntu@"${params.IP_ADDRESS}" << EOF
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
                    ssh  -i .ssh/id_rsa ubuntu@"${params.IP_ADDRESS}" << EOF
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
                    ssh  -i .ssh/id_rsa ubuntu@"${params.IP_ADDRESS}" << EOF
                    lsof -t -i:8080 | xargs kill -9
                    cd express-ejs 
                    forever start index.js 
                    exit 0
                    << EOF
                    """
                }
            
        }
    }

    }
    
}