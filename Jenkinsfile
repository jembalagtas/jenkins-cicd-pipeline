node ('master'){

    stage('Checkout')
        checkout poll: false, scm: [$class: 'GitSCM', branches: [[name: '*/master']], 
        doGenerateSubmoduleConfigurations: false, extensions: [], 
        submoduleCfg: [], userRemoteConfigs: [[credentialsId: '', 
        url: 'https://github.com/jareddeuna/spring-petclinic.git']]]

    stage('Build') {
        sh "mvn clean package"
    }
}
