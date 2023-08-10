pipeline {
  agent any
  stages {
    stage('build') {
      steps {
        sh 'mvn compile'
      }
    }

    stage('Run Tests') {
      parallel {
        stage('unit test') {
          steps {
            sh 'mvn test'
          }
        }

        stage('load test') {
          steps {
            sleep 4
          }
        }

      }
    }

    stage('package') {
      steps {
        sh 'mvn package -D skipTests'
        archiveArtifacts '**/*.jar'
      }
    }

  }
  tools {
    maven 'Maven 3.9.3'
    jdk 'JDK 20.0.2'
  }
  post {
    always {
      echo 'This pipeline is completed..'
    }

  }
}
