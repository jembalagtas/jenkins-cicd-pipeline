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
        sh "mv ${env.WORKSPACE}/target/petclinic.war ${env.WORKSPACE}/target/petclinic-${env.BUILD_ID}.war"
        sh "curl -v -u admin:admin --upload-file ${env.WORKSPACE}/target/petclinic-${env.BUILD_ID}.war http://wdcdmzyz22033182.ibmcloud.dst.ibm.com/nexus/content/repositories/PETCLINIC/petclinic-${env.BUILD_ID}.war"

    stage'Deploy'
        sh """
        echo '[target]' > ${env.WORKSPACE}/hosts
        echo '169.60.88.164' >> hosts

        ansible target -m ping
        """
}