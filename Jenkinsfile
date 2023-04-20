pipeline {
    environment
    {
    DIRECTORY_PATH="C:\\Temp" 
    TESTING_ENVIRONMENT="TestEnvironment"
    PRODUCTION_ENVIRONMENT="ProdEnvironment"
    }
    agent any
    stages
     {
     stage("Build") {
        steps {
                echo "This is the Build stage"
                echo "- Build the code using the Maven tool to compile and package your code"
        }
		}
    stage("Unit and Integration Tests") {
        steps {
                echo "running unit tests using the JUnit tool to ensure the code functions as expected and running integration tests using the TestComplete tool to ensure the different components of the application work together as expected"
        }
		success{
			mail to: "jeremysconway@hotmail.com",
            subject: "Unit and Integration Testing Successfully Completed",
            body: "Unit and Integration Testing Successfully Completed!!!" 
                 
                }
		}
	stage("Code Analysis") {
        steps {
                echo "The Code Analysis Tool Codacy has been integrated to analyse the code and ensure it meets industry standards "
        }
		}
	stage("Security Scan") {
        steps {
                echo "Performing a security scan on the code using the Tenable Nessus tool to identify any vulnerabilities"
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
            post{
                success{
                 mail to: "jeremysconway@hotmail.com",
                 subject: "Build Status Email",
                 body: "Build was Successful!!" 
                 
                }
            }
		}			
		}
}
