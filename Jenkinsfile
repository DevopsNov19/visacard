@Library('pipeline-library-demo')_
def greet(String name = 'human') {
 echo "GoodMorning, ${name}."
 
}


node('maven-label') {
   
   
   stage('Preparation') { // for display purposes
      
      git branch: '${branch}', url: 'https://github.com/DevopsNov19/visacard.git'
        
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
   
stage('sayhello') { 
  sayHello "Edureka"
 greet "Raj" 
   }   
   }
