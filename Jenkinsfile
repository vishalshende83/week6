pipeline {
     agent any
     stages {
          stage("Compile") {
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
                         if(env.GIT_BRANCH == "origin/main"){
                          echo "Inside - Code Coverage.Branch is : ${env.GIT_BRANCH}"
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