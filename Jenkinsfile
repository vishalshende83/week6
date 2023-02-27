podTemplate(containers: [
  containerTemplate(
    name: 'gradle',
    image: 'gradle:6.3-jdk14',
    command: 'sleep',
    args: '30d'
    ),
  ]) {
    node(POD_LABEL) {
      stage('Compile') {
	container('gradle') {
          stage('Build a gradle project') 
               steps {
                    sh "./gradlew compileJava"
               }
          stage('Unit test') {
	          steps {
                    sh "./gradlew test"
               }
          }
          stage('Code coverage') {
	          steps {
                    sh "./gradlew jacocoTestReport"
                    sh "./gradlew jacocoTestCoverageVerification"
               }
          }
          stage('Static code analysis') {
	          steps {
                    sh "./gradlew checkstyleMain"
					sh "./gradlew jacocoTestReport"
               }
          }
        }
      }   
    }
}
