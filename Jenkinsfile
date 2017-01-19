node {
   def mvnHome

   stage('Preparation') { // for display purposes
      // Get some code from a GitHub repository
      git credentialsId: '1b8af9e7-8cb3-422d-a55d-625e51db0953', url: 'https://maruhachi@bitbucket.org/projectLovelive/nico-demo.git'
      // Get the Maven tool.
      mvnHome = tool 'M3'
   }

   stage('Build') {
      // Run the maven build
      if (isUnix()) {
         sh "'${mvnHome}/bin/mvn' -Dmaven.test.failure.ignore clean package"
      } else {
         bat(/"${mvnHome}\bin\mvn" -Dmaven.test.failure.ignore clean package/)
      }
   }

   stage('Results') {
      archive 'target/*.jar'
   }
}
