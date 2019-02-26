pipeline{

agent { label 'master'}

tools{
	
	maven 'MAVEN3'
	jdk 'JAVA8'
	
}

 stages{
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
