//SCRIPTED PIPELINE
// node {	
// 		echo "Build"	
// 		echo "Test"		
// 		echo "Integration Test"	
// }

//DECLARATIVE PIPELINE
pipeline{
	 agent any
	//agent { docker {image 'maven:3.6.3'}}
	environment {
		dockerHome = tool 'myDocker'
		mavenHome = tool 'myMaven'
		PATH = "$dockerHome/bin:$mavenHome/bin:$PATH"
	}
	stages{
		stage('Checkout'){
			steps{
				sh 'mvn --version'
				sh 'docker version'
				echo "Build"	
				echo "PATH - $PATH"
				echo "BUILD NUMBER - $env.BUILD_NUMBER"
				echo "BUILD_ID - $env.BUILD_ID"
				echo "JOB_NAME -  $env.JOB_NAME"
				echo "BUILDTAG - $env.BUILDTAG"
				echo "BUILD_URL - $env.BUILD_URL"
			}
		}

		stage('Compile'){
			steps{
				sh "mvn clean compile"
			}
		}
		stage('Test'){
			steps{
				echo "mvn test"	
			}
		}
		stage('Integration Test'){
			steps{
				echo "mvn failsafe:integration-test failsafe:verify"	
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