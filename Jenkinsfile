pipeline {
    agent any
    tools{
    maven "maven3.8.4"
    } 
    stages{
    stage('1.clone'){
      steps{
            sh "echo clonning the latest version of the code" 
            git branch: 'feature', credentialsId: 'Git_Credentials', url: 'https://github.com/jjohnbosco5/docker-jenkins'
            sh "echo clonning successful"
        }
    }
    stage('2.Build'){
      steps{
        sh "echo validation, compilation, testing and package"
        sh "echo testing successful and ready to package"
        sh "mvn clean package"
      }
    ]
    stage('3.Deploy2UAT'){
      steps{
        sh "echo DEPLOYING TO Production"
        sshagent(['agentcredentials']) {
        sh "scp -o StrictHostKeyChecking=no target/*.war ec2-user@18.234.217.66:/opt/tomcat9/webapps/uatapp.war"
      }
    }
  }
  } 
    post{
    always{
      mail bcc: 'jjohnbosco5@gmail.com', body: '''Success,
