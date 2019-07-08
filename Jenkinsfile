node ('ansible'){
    deleteDir()
    stage'Checkout'
        checkout poll: false, scm: [$class: 'GitSCM', branches: [[name: '*/master']], 
        doGenerateSubmoduleConfigurations: false, extensions: [], 
        submoduleCfg: [], userRemoteConfigs: [[credentialsId: '', 
        url: 'https://github.com/jembim/spring-framework-petclinic.git']]]

    stage'Build'
        sh "mvn clean package"

    stage'Unit Testing'
        sh "mvn test"

    stage'Code Quality'
        def scannerHome = tool 'SonarScanner 2.4';
        withSonarQubeEnv('SonarQube Server') {
            sh "${scannerHome}/bin/sonar-scanner"
        }

    stage'Publish'
        sh "mv ${env.WORKSPACE}/target/petclinic.war ${env.WORKSPACE}/target/petclinic-${env.BUILD_ID}.war"
        sh "curl -v -u admin:admin --upload-file ${env.WORKSPACE}/target/petclinic-${env.BUILD_ID}.war http://wdcdmzyz22033182.ibmcloud.dst.ibm.com/nexus/content/repositories/PETCLINIC/petclinic-${env.BUILD_ID}.war"
}