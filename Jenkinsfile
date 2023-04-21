pipeline {
    agent any
    stages
     {
     stage("Build") {
        steps {
                echo "This is the Build stage"
                echo "Build the code using the Maven tool to compile and package the code"
        }
		}
    stage("Unit and Integration Tests") {
        steps {
                echo "running unit tests using the JUnit tool to ensure the code functions as expected and running integration tests using the TestComplete tool to ensure the different components of the application work together as expected"
        }
		post {
		success{
				 emailext attachLog: true, body: "${currentBuild.result}: ${BUILD_URL}", compressLog: true, replyTo: 'jeremysconway@gmail.com',
      			 subject: "Unit and Integration Testing Successful: ${JOB_NAME}-Build# ${BUILD_NUMBER} ${currentBuild.result}", to: 'jeremysconway@hotmail.com'			
                }
		failure{
				 emailext attachLog: true, body: "${currentBuild.result}: ${BUILD_URL}", compressLog: true, replyTo: 'jeremysconway@gmail.com',
      			 subject: "Unit and Integration Testing Failed: ${JOB_NAME}-Build# ${BUILD_NUMBER} ${currentBuild.result}", to: 'jeremysconway@hotmail.com'	       
               }
		}
		}
	stage("Code Analysis") {
        steps {
                echo "The Code Analysis Tool Codacy has been integrated to analyse the code and ensure the code meets industry standards "
        }
		}
	stage("Security Scan") {
        steps {
                echo "Performing a security scan on the code using the Tenable Nessus tool to identify any vulnerabilities"
        }
		post {
		success{
				 emailext attachLog: true, body: "${currentBuild.result}: ${BUILD_URL}", compressLog: true, replyTo: 'jeremysconway@gmail.com',
      			 subject: "Security Scan Testing Successful: ${JOB_NAME}-Build# ${BUILD_NUMBER} ${currentBuild.result}", to: 'jeremysconway@hotmail.com'	        
                }
		failure{
				 emailext attachLog: true, body: "${currentBuild.result}: ${BUILD_URL}", compressLog: true, replyTo: 'jeremysconway@gmail.com',
      			 subject: "Security Scan Testing Failed: ${JOB_NAME}-Build# ${BUILD_NUMBER} ${currentBuild.result}", to: 'jeremysconway@hotmail.com'	        
               }
		}
		}	
	stage("Deploy to Staging") {
        steps {
                echo "Deploying the application to the AWS EC2 staging instance using AWS CloudFormation"
        }
		}	
	stage("Integration Tests on Staging") {
        steps {
                echo "Running integration tests using the TestComplete tool on the staging environment to ensure the application functions as expected in a production-like environment."
        }
		}	
	stage("Deploy to Production") {
        steps {
                echo "Deploying the application to a AWS EC3 production instance using AWS CloudFormation"
        }
		}			
		}
}
