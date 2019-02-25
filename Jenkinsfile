pipeline{

agent { label 'master'}

tools{
	
	maven 'MAVEN3'
	jdk 'JAVA8'
	
}

 stages{
		stage('preparing the code'){
            steps{			
			 echo "get the code from git hub "
			 git changelog: false, credentialsId: 'b492b511-c25d-4f1e-bf5a-1d268c4937b1', poll: false, url: 'https://github.com/Rajakumarhub/My_web_application_1.git'			 
			}
		}
		stage('Doing maven build'){
			steps{
		        echo "performing maven build"
				bat 'mvn -Dmaven.test.failure.ignore clean package'
            }
		}
		stage('Artifacts'){
			steps{
		        echo "performing archival of artifacts "
				archiveArtifacts 'target/*.war'
			}
		}
		stage ('Sending notification email'){
			steps{
				echo " sending the email "
				emailext attachLog: true, body: 'This is  a build notification mail from Jenkins ', subject: 'Jenkins build notification', to: 'rajakumar5999@gmail.com'
			}
		}
   }
}