#!/usr/bin/env groovy
node {
    properties([buildDiscarder(logRotator(artifactNumToKeepStr: '10')), [$class: 'ScannerJobProperty', doNotScan: false]])
    stage('Checkout from Git') {
        echo 'Cloning the repo'
        git credentialsId: 'git-id', url: 'https://github.com/abhinav9842/maven-project'

    }
    stage('maven install') {
        echo 'maven install'
        sh '''pwd
            ls -alh
            mvn install'''
    }
    stage('maven deploy to nexus'){
     sh '''
     pwd 
     ls -alhR
     mvn deploy:deploy-file -DgroupId=com.example.maven-project -DartifactId=maven-project -Dversion=1.0.0 -DgeneratePom=true -Dpackaging=jar -DrepositoryId=nexus -Durl=http://nexus:8081/repository/maven-releases/ -Dfile=server/target/server.jar
    '''
    }

} 
