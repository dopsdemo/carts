pipeline {
  agent {
    docker {
      image 'schoolofdevops/carts-maven:3.9'
    }

  }
  stages {
    stage('build') {
      environment { 
                JAVA_HOME = /opt/java/openjdk
            }
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
 
  post {
    always {
      echo 'This pipeline is completed..'
    }

  }
}
