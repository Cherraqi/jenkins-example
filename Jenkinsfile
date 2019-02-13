node {
   def mvnHome
   stage('Get code from Gitlab repository') { // for display purposes
      // Get some code from a Gitlab repository
      git 'https://gitlab.com/Cherrraqi/projetdevops.git'
      // Get the Maven tool.
      // ** NOTE: This 'M3' Maven tool must be configured
      // **       in the global configuration.           
      mvnHome = tool 'M3'
   }
   stage('Build') {
      // Run the maven build
         sh "'${mvnHome}/bin/mvn'  clean"
         sh "'${mvnHome}/bin/mvn'  package"
      }
    stage ('TEST') {
                
                sh "'${mvnHome}/bin/mvn' test"
		always {
                	junit 'server/target/surefire-reports/*.xml'
                	}
                sh "'${mvnHome}/bin/mvn' test checkstyle:checkstyle"
             
         }

   
   stage('Results') {
      junit '**/target/surefire-reports/TEST-*.xml'
      archive 'target/*.jar'
   }
}
