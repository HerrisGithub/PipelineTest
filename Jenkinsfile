pipeline {
  agent any
  stages {
    stage("SCM"){
      steps {
        script {
          try {
            git branch: 'main', credentialsId: 'ef42a039-acc0-417d-8985-977114546084', url: 'https://github.com/HerrisGithub/PipelineTest.git'
            author = ""
            email = ""
            commitId = ""
            date = ""
            // def author = ""
            // def changeSet = currentBuild.rawBuild.changeSets               
            // for (int i = 0; i < changeSet.size(); i++) 
            // {
            //     def entries = changeSet[i].items;
            //     for (int j = 0; j < changeSet.size(); j++) 
            //     {
            //         def entries2 = changeSet[j].items;
            //         def entry = entries2[0]
            //         author += "${entry.author}"
            //     } 
            // }
            if(currentBuild.changeSets && currentBuild.changeSets[0].items){
                item = currentBuild.changeSets[0].items[0];
                author = item.author.fullName
                // email = item.authorEmail
                commitId = item.commitId
                // comment = item.comment
                date = new Date( item.timestamp ).toString()
            }
            echo "Author is ${author}"
            echo "Author is ${currentBuild.changeSets[0].items[0].author.fullName}"
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