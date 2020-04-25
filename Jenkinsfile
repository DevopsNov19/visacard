node('maven-label') {
   
   
   stage('Preparation') { // for display purposes
      
      git 'https://github.com/jglick/simple-maven-project-with-tests.git'
        
      mvnHome = tool name: 'maven-3.3.9', type: 'maven'
   }
   stage('Build') {
      
      if (isUnix()) {
         sh "'${mvnHome}/bin/mvn' clean install"
      } else {
         bat(/"${mvnHome}\bin\mvn" -Dmaven.test.failure.ignore clean package/)
      }
   }
   stage('Results') {
      junit '**/target/surefire-reports/TEST-*.xml'
      archive 'target/*.jar'
   }
   }
