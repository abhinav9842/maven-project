#!/usr/bin/env groovy
node {
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
     mvn deploy:deploy-file -DgroupId=com.example.maven-project -DartifactId=maven-project -Dversion=1.0.0 -DgeneratePom=true -Dpackaging=jar -DrepositoryId=nexus -Durl=http://192.168.1.23:8081/repository/abhinav_docker/ -Dfile=server/target/server.jar
    '''
    }

} 
