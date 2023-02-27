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
               if (env.GIT_BRANCH == "origin/main") {
               steps {
                    sh 'printenv'
                    
                         sh "./gradlew jacocoTestReport"
                         sh "./gradlew jacocoTestCoverageVerification"
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