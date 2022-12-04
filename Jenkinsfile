pipeline {
 environment {
 imagename = "ssasi2424/simplilearnproject1"
 registryCredential = 'ssasi2424'
 dockerImage = ''
 }
 agent any
 stages {
 stage('Cloning Git') {
 steps {
 git([url: 'https://github.com/kinjansarath/sarathproj1.git', branch: 'main'])
 }
 }
 stage('Building image') {
 steps{
 script {
 dockerImage = docker.build imagename

 }
 }
 }
 stage(‘Running image’) {
 steps{
 script {
 sh "docker run ${imagename}:latest"
 }
 }
 }
 stage('Deploy Image') {
 steps{
 script {
 docker.withRegistry( '', registryCredential ) {
 dockerImage.push("$BUILD_NUMBER")
 dockerImage.push('latest')
 }
 }
 }
 }
 }
}
