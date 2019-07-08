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

    stage'Publish'
        sh "mv /workspace/petclinic/target/petclinic.war /workspace/petclinic/target/petclinic-${BUILD_ID}.war"
        sh "curl -v -u admin:admin --upload-file /workspace/petclinic/target/petclinic.war http://wdcdmzyz22033182.ibmcloud.dst.ibm.com/nexus/content/repositories/PETCLINIC/petclinic-${BUILD_ID}.war"
}