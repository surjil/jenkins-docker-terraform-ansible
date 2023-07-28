pipeline {
  agent any
  stages {
    stage('Compile') {
      steps {
        script{
                def mvnHome = tool name: 'MAVEN_HOME', type: 'maven'
                sh "${mvnHome}/bin/mvn package"
        }
      }
    }
    stage('Building Docker Image') {
      steps{
        script {
          sh "docker build -t surjil1612/cicd-poc-jenkins-ansible ss:$BUILD_NUMBER ."
        }
      }
    }
    stage('Push Image To Docker Hub') {
      steps{
        script {
          sh "echo $USER"
          sh "docker login -u surjil1612 -p Ajushaik4087"
          sh "docker push surjil/cicd-poc-jenkins-ansible ss:$BUILD_NUMBER"
          }
        }
      }
    }
}

