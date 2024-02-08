node {
    properties([pipelineTriggers([pollSCM('* * * * *')])])
    stage('Checkout') {
        git branch: 'main', url: 'https://github.com/isav48/jgsu-spring-petclinic.git'
    }
    stage('Build') {
        if (isUnix()) {
            sh('./mvnw clean package')
        }
    }
    stage('Results') {
        junit('**/target/surefire-reports/*.xml')
        archiveArtifacts('target/*.jar')
    }
}