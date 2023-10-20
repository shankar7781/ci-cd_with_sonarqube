@Library('my-shared-library') _
pipeline {
  agent any
  stages {
    stage("git checkout"){
          steps{
            
               gitCheckout(
                 branch:"master",
                 url:"https://github.com/shankar7781/ci-cd_with_sonarqube.git"
               )
            
          }
    }

    stage('Unit Test maven'){
         
         when { expression {  params.action == 'create' } }

            steps{
               script{
                   
                   mvnTest()
               }
            }
        }
  }
}
