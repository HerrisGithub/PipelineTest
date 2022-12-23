pipeline {
  agent any
  environment {
     author = ""
     commitId = ""
     date = ""
     result = "PROCESS"
     comment = ""
  }
  stages {
    stage("SCM"){
      steps {
        git branch: 'main', credentialsId: 'ef42a039-acc0-417d-8985-977114546084', url: 'https://github.com/HerrisGithub/PipelineTest.git'
        script {
          try {
           sh 'curl -X POST https://pin.waruna.id/jenkins/build-start?ProjectName=pipeline'
          } catch (exc) {
            currentBuild.result = 'FAILURE'
          }
        }
      }
    }
    stage("Build"){
      steps {
        script {
          try {
            // sh 'npm install'
            echo 'test';
          } catch (exc) {
            echo "error install"
            result = 'FAIL'
          }
        }
      }
    }
    stage ('Deploy') {
      steps{
       echo 'sudah berhasil'
      }
    }
  }
  post {
        always {
           echo 'a'
           sh 'curl -X POST https://pin.waruna.id/jenkins/build-end?ProjectName=pipeline'
        }
        success {
            echo "Success"
        }
        failure {
            echo "I FAILED"
        }
        cleanup {
            echo "I RAN ANYWAY"
        }
    }
}