#!/usr/bin/env groovy
node {
    stage('Checkout from Git') {
        echo 'Cloning the repo'
        git credentialsId: 'git-id', url: 'https://github.com/abhinav9842/maven-project'

    }
    stage('maven install') {
        echo 'maven install'
        sh '''pwd
            mvn install'''
    }

} 