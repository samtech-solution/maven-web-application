node {

    def mavenHome = tool name: 'maven3'
    properties([buildDiscarder(logRotator(artifactDaysToKeepStr: '', artifactNumToKeepStr: '5', daysToKeepStr: '', numToKeepStr: '3')), pipelineTriggers([pollSCM('* * * * *')])])

    stage('CheckOutCode') {
        git branch: 'development', credentialsId: 'git-credential', url: 'https://github.com/samtech-solution/maven-web-application.git'
    }

    stage('Build') {
        sh "${mavenHome}/bin/mvn clean package"
    }
/*
    stage('ExecuteSonarQubeReport') {
        sh "${mavenHome}/bin/mvn clean sonar:sonar"
    }
*/
    stage('UploadArtifactIntoNexus') {
        sh "${mavenHome}/bin/mvn clean deploy"
    }

    
}
