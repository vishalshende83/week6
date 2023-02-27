podTemplate(containers: [
  containerTemplate(
    name: 'gradle',
    image: 'gradle:6.3-jdk14',
    command: 'sleep',
    args: '30d'
    ),
  ]) {
    node(POD_LABEL) {
      stage('Run pipeline against a gradle project - test MAIN') {
	container('gradle') {
          stage('Build a gradle project') {
            echo "I am the branch"
            sh "./gradlew test"
          }
          stage('Code coverage') {
	       echo "My CC branch is: "
            sh "./gradlew jacocoTestReport"
            sh "./gradlew jacocoTestCoverageVerification"
            
          }
        }
      }   
    }
}
