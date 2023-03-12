pipeline {
     agent any
     stages {
          stage("Build") {
               steps {
                    sh "./gradlew compileJava"
               }
          }
          stage("Unit test") {
               steps {
                    sh "./gradlew test"
               }
          }
          stage("Code coverage") {
               steps {
                    script{
                         if(env.BRANCH_NAME == "main"){
                          echo "Inside - Code Coverage.Branch is : ${env.BRANCH_NAME}"
                         sh "./gradlew jacocoTestReport"
                         sh "./gradlew jacocoTestCoverageVerification"
                         }
                         else{
                              echo "Skipping Stage - Code Coverage"
                         }
                    }
               }
          }
          stage("Static code analysis") {
               steps {
                    sh "./gradlew checkstyleMain"
                    sh "./gradlew jacocoTestReport"
               }
          }
          
     }
}