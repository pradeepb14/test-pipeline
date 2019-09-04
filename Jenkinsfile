node{
      def mvnHome = tool name: 'maven 3.6.1', type: 'maven' 
      stage('Checkout'){
         git 'https://github.com/pradeepb14/test-pipeline'
       
      }  
      stage('Build'){
         //// Get maven home path and build
        sh "${mvnHome}/bin/mvn clean package -Dmaven.test.skip=true"
      }
     stage ('Test-JUnit'){
         sh "'${mvnHome}/bin/mvn' test surefire-report:report"
      }  
    
      stage('Deploy') {     
          sshagent(['Admincssindiaonline']) {
               sh 'scp -o StrictHostKeyChecking=no target/demojavapipeline_newuser.war jenkins@3.106.56.70:/opt/apache-tomcat-8.5.45/webapps'
              
          }
         
     }
      
 }
