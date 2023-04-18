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
                bat "java --version"
                echo "fetch the source code from the directory path ${DIRECTORY_PATH}"
                echo "compile the code and generate any necessary artifacts"
        }
		}
    stage("Test") {
        steps {
                echo "This is the test stage"
                echo "unit tests"
                echo "integration tests"
        }
		}
	stage("Code Quality Check") {
        steps {
                echo "This is the Code Quality Check stage"
                echo "check the quality of the code"
        }
		}
	stage("Deploy") {
        steps {
                echo "This is the Deploy stage"
                echo "deploy the application to a testing environment: ${TESTING_ENVIRONMENT}"
        }
		}	
	stage("Approval") {
        steps {
                echo "This is the Approval stage"
                echo "The pipeline must pause for 10 seconds before continuing"
                sleep 10
        }
		}	
stage("Deploy to Production") {
        steps {
                echo "This is the Deploy to Production stage"
                echo "Deploy the code to the production environment: ${PRODUCTION_ENVIRONMENT}"
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
