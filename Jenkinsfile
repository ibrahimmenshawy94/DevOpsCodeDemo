
pipeline{
    tools{
       
        maven 'mymaven'
    }
	agent any
      stages{
           stage('Checkout'){
	    
               steps{
		 echo 'cloning'
                 git 'https://github.com/Sonal0409/DevOpsClassCodes.git'
              }
          }
          stage('Compile'){
             
              steps{
                  echo 'complie the code..'
                  sh 'mvn compile'
	      }
          }
          stage('CodeReview'){
		  
              steps{
		    
		  echo 'codeReview'
                  sh 'mvn pmd:pmd'
              }
          }
           stage('UnitTest'){
		  
              steps{
	         
                  sh 'mvn test'
              }
          
          }
        
          stage('Package'){
		  
              steps{
		  
                  sh 'mvn package'
              }
          }
	     
          
      post {
        always {
            // Archive artifacts or perform other cleanup tasks
            archiveArtifacts 'target/*.jar'
        }
        success {
            // Notify relevant stakeholders of successful build and test results
            emailext body: 'Unit tests passed. Build successful!',
                    subject: 'Build and Unit Test Status - SUCCESS',
                    to: 'henamensho@gmail.com' // Specify the email address of the recipient
        }
        failure {
            // Notify relevant stakeholders of failed build or test results
            emailext body: 'Unit tests failed. Build failed.',
                    subject: 'Build and Unit Test Status - FAILURE',
                    to: 'henamensho@gmail.com' // Specify the email address of the recipient
        }
    }
}
