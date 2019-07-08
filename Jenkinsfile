pipeline {
    agent { label 'ansible' }
    stages {
        stage('Build') {
            steps {
                cleanWs()
                checkout poll: false, scm: [$class: 'GitSCM', branches: [[name: '*/master']], 
                doGenerateSubmoduleConfigurations: false, extensions: [], 
                submoduleCfg: [], userRemoteConfigs: [[credentialsId: '', 
                url: 'https://github.com/jareddeuna/spring-petclinic.git']]]   
 
                sh '''#!/bin/bash
                    mvn
                    mvn clean package
                '''
            }
        }   
    }
} 
