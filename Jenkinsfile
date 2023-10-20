@Library("my-shared-library")
pipeline {
  agent any
  stages {
    stage("git checkout"){
          steps{
            
               gitCheckout(
                 branch:"main",
                 url:"https://github.com/shankar7781/ci-cd_with_sonarqube.git"
               )
            
          }
    }
  }
}
