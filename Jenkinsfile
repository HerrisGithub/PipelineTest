pipeline {
  agent any
  stages {
    stage("SCM"){
      steps {
        script {
          try {
            echo "Semua Value ${currentBuild.changeSets.toString()}"
            echo "Build number is ${currentBuild.number}"
            echo "Result is ${currentBuild.result}"
        //    sh 'curl -X POST https://pin.waruna.id/jenkins/build-start?ProjectName=pipeline'
           git branch: 'main', credentialsId: 'ef42a039-acc0-417d-8985-977114546084', url: 'https://github.com/HerrisGithub/PipelineTest.git'
          } catch (exc) {
            echo "Error SCM: ${exc.toString()}"
            result = 'FAIL'
            currentBuild.result = 'FAILURE'
          }
        }
      }
    }
    stage("Build"){
      steps {
        script {
          try {
            sh 'npm install'
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
        //    sh 'curl -X POST https://pin.waruna.id/jenkins/build-end?ProjectName=pipeline'
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