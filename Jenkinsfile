pipeline {
  agent any
  environment {
     author = ""
     commitId = ""
     date = ""
     changeSets
  }
  stages {
    stage("SCM"){
      steps {
        git branch: 'main', credentialsId: 'ef42a039-acc0-417d-8985-977114546084', url: 'https://github.com/HerrisGithub/PipelineTest.git'
        script {
          try {
            if(currentBuild.changeSets && currentBuild.changeSets[0].items){
                changeSets = currentBuild.changeSets;
                // def item = currentBuild.changeSets[0].items[0]
                // item = currentBuild.changeSets[0].items[0];
                author = changeSets.items[0].author.fullName
                // email = item.authorEmail
                commitId =  currentBuild.changeSets[0].items[0].commitId
                // comment = item.comment
                date = new Date(currentBuild.changeSets[0].items[0].timestamp ).toString()
            }
            echo "Author is ${author}"
            echo "Build number is ${currentBuild.number}"
            echo "Result is ${currentBuild.result}"
            echo "Date is ${date}"
        //    sh 'curl -X POST https://pin.waruna.id/jenkins/build-start?ProjectName=pipeline'
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