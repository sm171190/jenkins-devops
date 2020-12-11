//SCRIPTED PIPELINE
// node {	
// 		echo "Build"	
// 		echo "Test"		
// 		echo "Integration Test"	
// }

//DECLARATIVE PIPELINE
pipeline{
	// agent any
	agent { docker {image 'maven:3.6.3'}}
	stages{
		stage('Build'){
			steps{
				sh 'mvn --version'
				echo "Build"	
			}
		}
		stage('Test'){
			steps{
				echo "Test"	
			}
		}
		stage('Integration Test'){
			steps{
				echo "Integration Test"	
			}
		}

	} 
	post{
		always {
			echo "I'm awesome. I run always."
		}
		success{
			echo "I run when you are successful."
		}
		failure{
			echo "I run when you fail."
		}
		// unstable{
		// 	echo "I run when a test failure happens."
		// }
		//changed{
		//	echo "I run when the build status changes."
		//}
	}		
}