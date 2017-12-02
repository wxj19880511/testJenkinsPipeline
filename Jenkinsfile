pipeline {
  agent {
    docker {
      image 'hello-world'
    }
    
  }
  stages {
    stage('Initialize') {
      steps {
        sh 'echo "initialize ..."'
      }
    }
    stage('Building') {
      parallel {
        stage('x86_64') {
          steps {
            sh 'echo "Linux_x86_64 building"'
          }
        }
        stage('X86_32') {
          steps {
            sh 'echo "Linux_x86_32 building"'
          }
        }
        stage('ppc') {
          steps {
            sh 'echo "ppc building"'
          }
        }
      }
    }
    stage('UT') {
      steps {
        echo 'UT'
      }
    }
    stage('MT') {
      steps {
        sh 'echo "MT"'
      }
    }
    stage('Report') {
      steps {
        input(message: 'Are you sure to report?', ok: 'Yes')
      }
    }
  }
  environment {
    AZ = 'hz_bts'
  }
}