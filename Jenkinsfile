node
{
  echo "dev Job....."
def mavenHome = tool name : "maven3.8.4"

properties([buildDiscarder(logRotator(artifactDaysToKeepStr: '', artifactNumToKeepStr: '', daysToKeepStr: '', numToKeepStr: '5')), [$class: 'RebuildSettings', autoRebuild: false, rebuildDisabled: false], [$class: 'JobLocalConfiguration', changeReasonComment: ''], pipelineTriggers([pollSCM('* * * * *')])])

stage('checkoutCode'){
git branch: 'development', credentialsId: 'e21eed53-83d9-470e-b1af-29220c5de83a', url: 'https://github.com/kiranvedaHP/maven-web-application.git'
}

stage('Build'){
sh "${mavenHome}/bin/mvn clean package"
}
/*
stage('ExecuteSonarQubeReport'){
sh "${mavenHome}/bin/mvn sonar:sonar"
}

stage('UploadArtifactsIntoNexus'){
sh "${mavenHome}/bin/mvn deploy"
}

stage('DeployApplicationtoTomcatServer'){

sshagent(['82627b85-dd20-471a-93b6-fc5ee431350d']) {
  sh "scp -o StrictHostKeyChecking=no target/maven-web-application.war
ec2-user@3.110.155.182:/opt/apache-tomcat-9.0.54/webapps/"
}
}

stage('SendEmailNotification'){

emailext body: '''Regards,
Kiran''', subject: 'Buildover', to: 'kiranhp72@gmail.com'
}
*/
}
