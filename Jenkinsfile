node ('ansible'){

    stage'Checkout'
        checkout poll: false, scm: [$class: 'GitSCM', branches: [[name: '*/master']], 
        doGenerateSubmoduleConfigurations: false, extensions: [], 
        submoduleCfg: [], userRemoteConfigs: [[credentialsId: '', 
        url: 'https://github.com/spring-petclinic/spring-framework-petclinic.git']]]

    stage'Build'
        sh "mvn clean package"

    stage'Unit Testing'
        sh "mvn test"
}