pipeline {
  agent {
    label 'slave1'
  }
  stages {
    stage('GetCode') {
      steps {
        git 'https://github.com/Sharath8000/hello-world.git'
      }
    }

    stage('SonarQube analysis') {
      steps {
        withSonarQubeEnv('sonarqube') {
          sh 'mvn sonar:sonar'
        }

      }
    }

    stage('Docker image build') {
      steps {
        sh 'mvn clean deploy'
      }
    }

  }
}