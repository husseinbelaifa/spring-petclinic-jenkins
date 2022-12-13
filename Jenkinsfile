pipeline {
    agent any

     environment {
         branch = "${env.GIT_BRANCH.split("/")[1]}"

      }

//    triggers {
//      pollSCM '* * * * *'
//    }


    stages {

        stage("checkout"){
            steps {

                git url: 'git@github.com:husseinbelaifa/spring-petclinic-jenkins.git', branch: 'DEV'

                echo "branch name is ${env.GIT_BRANCH.split("/")[1]}"

                echo "currentBuild is ${currentBuild.currentResult}"



            }

        }




//         stage('Build') {
//             steps {
//
//
//                 sh "./mvnw clean package"
//
//                  echo "BRANCH_NAME: ${env.GIT_BRANCH.split("/")[1]}"
//
//                   echo "BRANCH_NAME: ${env.GIT_BRANCH}"
//             }
//
//
//
//             post {
//                 // If Maven was able to run the tests, even if some of the test
//                 // failed, record the test results and archive the jar file.
//                 always {
//                     junit '**/target/surefire-reports/TEST-*.xml'
//                     archiveArtifacts 'target/*.jar'
//                 }
//             }
//         }



        stage('STAGING'){

           when {


                  expression { branch == 'DEV' }
           }
          steps {
                  echo 'run this stage - ony if the branch = DEV branch'
              }

        }


         stage('DEPLOY_MASTER'){

                   when {


                            branch 'main'
                   }
                  steps {
                          echo 'DEPLOY FOR MASTER'
                      }

        }


         stage('DEPLOY_DEV'){

                   when {


                          branch 'DEV'
                   }
                  steps {
                          echo 'DEPLOY FOR DEV'
                      }

         }


    }
}
