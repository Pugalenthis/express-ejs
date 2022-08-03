pipeline {
    agent any
    parameters {
         string(name: 'express-ejs', defaultValue: '52.66.205.55', description: 'Staging Server')
    }

    triggers {
         pollSCM('* * * * *')
     }

stages{
    stage ("Deploy to Production"){
        steps {
            sh script:'''
                #!/bin/bash
                echo "This is start $(pwd)"
                cd express-ejs
                echo "This is start $(pwd)"
                git pull origin main
            '''
            }
            
        }
    }
}