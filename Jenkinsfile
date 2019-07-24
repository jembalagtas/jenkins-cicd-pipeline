node ('ansible'){
    deleteDir()
    stage'Build'
        // checkout poll: false, scm: [$class: 'GitSCM', branches: [[name: '*/master']], 
        // doGenerateSubmoduleConfigurations: false, extensions: [], 
        // submoduleCfg: [], userRemoteConfigs: [[credentialsId: '', 
        // url: 'https://github.com/jembim/spring-framework-petclinic.git']]]

        // sh "mvn clean package"
        sh "echo 'Building'"
        sh "sleep 30"
        

    stage'Unit Test'
        // sh "mvn test"
        sh "echo 'Unit testing'"
        sh "sleep 20"

    stage'Code Quality'
        // def scannerHome = tool 'SonarScanner';
        // sh "${scannerHome}/bin/sonar-scanner"
        sh "echo 'Static Code Analysis'"
        sh "sleep 40"

    stage'Publish'
        // sh "mv /workspace/pipeline/target/petclinic.war /workspace/pipeline/target/petclinic-${env.BUILD_ID}.war"
        // sh "curl -v -u admin:admin --upload-file /workspace/pipeline/target/petclinic-${env.BUILD_ID}.war http://wdcdmzyz22033182.ibmcloud.dst.ibm.com/nexus/content/repositories/PETCLINIC/petclinic-${env.BUILD_ID}.war"
        sh "echo 'Publishing to Artifact'"
        sh "sleep 10"

    stage'Deploy'
        // checkout changelog: false, poll: false, scm: [$class: 'GitSCM', branches: [[name: '*/master']], 
        // doGenerateSubmoduleConfigurations: false, 
        // extensions: [[$class: 'RelativeTargetDirectory', relativeTargetDir: 'ansible']], 
        // submoduleCfg: [], userRemoteConfigs: [[url: 'https://github.com/jembim/ansible-cicd-pipeline.git']]]

        // sh """
        // echo "wdcdmzyz22033182" > /workspace/pipeline/ansible/hosts
        // cd /workspace/pipeline/ansible
        // ansible-playbook -i hosts -u jembalagtas --become --become-user root -e "target=wdcdmzyz22033182 build_id=${env.BUILD_ID}" master.yml
        // """
        sh "echo 'Deploying Artifact'"
        sh "sleep 20"
}