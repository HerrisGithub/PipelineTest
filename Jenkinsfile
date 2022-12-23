pipeline {
  agent any
  stages {
    stage("Github"){
      steps {
        script {
          try {
            echo GIT_COMMIT %GIT_COMMIT% 
            echo GIT_BRANCH %GIT_BRANCH%
            echo GIT_LOCAL_BRANCH %GIT_LOCAL_BRANCH%
            echo GIT_PREVIOUS_COMMIT %GIT_PREVIOUS_COMMIT%
            echo GIT_PREVIOUS_SUCCESSFUL_COMMIT %GIT_PREVIOUS_SUCCESSFUL_COMMIT%
            echo GIT_URL %GIT_URL%
            echo GIT_URL_N - %GIT_URL_N%
            echo GIT_AUTHOR_NAME %GIT_AUTHOR_NAME%
            echo GIT_COMMITTER_EMAIL %GIT_COMMITTER_EMAIL%
        //    sh 'curl -X POST https://pin.waruna.id/jenkins/build-start?ProjectName=pipeline'
           git branch: 'main', credentialsId: 'ef42a039-acc0-417d-8985-977114546084', url: 'https://github.com/HerrisGithub/PipelineTest.git'
          } catch (exc) {
            echo "error"
            result = 'FAIL'
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