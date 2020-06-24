node {
   stage('SCM') { // for display purposes
      // Get some code from a GitHub repository
      git 'https://github.com/spectrumqube/jenkins-pl-demo.git'     
   }
   stage('Build') {
      // Run the maven build
      withMaven(maven: 'mvn-3.6.3') {
         sh 'mvn -B -DskipTests clean package'
      }
   }
   stage('Build') {
      // Run the maven build
      withMaven(maven: 'mvn-3.6.3') {
         sh 'mvn test'
      }   
   }
   stage('Results') {
      // Publish results
      junit 'target/surefire-reports/*.xml'
      archiveArtifacts 'target/*.jar'
   }
   stage('Deliver') {
      // Deliver
      sh './jenkins/scripts/deliver.sh'
   }
}
