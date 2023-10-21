@Library('my-shared-library') _


pipeline{

    agent any
    parameters{

        choice(name: 'action', choices: 'create\ndelete', description: 'Choose create/Destroy')
        string(name: 'ImageName' , description: "name of the docker build" , defaultvalue: 'javaapp123')
        string(name: 'ImageTag' , description: "name of the docker build" , defaultvalue: 'v1')
        string(name: 'Appname' , description: "name of the docker build" , defaultvalue: 'springboot')
    }
    
    stages{
           stage('Git Checkout'){
                when { expression {  params.action == 'create' } }
            steps{
                gitCheckout(
                    branch: "main",
                    url: "https://github.com/shankar7781/ci-cd_with_sonarqube.git"
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
            stage('Integration Test maven'){
                 when { expression {  params.action == 'create' } }
               steps{
                    script{
                       mvnIntegrationTest()
                    }
                }
            }
            stage('static code analysis'){
                 when { expression {  params.action == 'create' } }
               steps{
                    script{
                       def SonarQubecredentialsId = 'sona' 
                       staticCodeAnalysis(SonarQubecredentialsId )
                    }
                }
            }
            stage('Quality gate status:sonar'){
                 when { expression {  params.action == 'create' } }
               steps{
                    script{
                       def SonarQubecredentialsId = 'sona' 
                       QualityGateStatus(SonarQubecredentialsId )
                    }
                }
            }
            stage('Maven build: maven'){
                 when { expression {  params.action == 'create' } }
               steps{
                    script{
                        mvnBuild()
                    }
                }
            }
            
    }

}
