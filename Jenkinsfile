//scripted
// node {
// 	stage('Build') { // stages are optional but they do make the file more readable.
// 		echo "Build"
// 	}
// 	stage('Test') {
// 		echo "Test"
// 	}
// 	stage('Integration Test') {
// 		echo "Integration Test "
// 	}
// }

//Declarative

pipeline {
    agent any
    //agent { docker { image 'maven:3.6.3'} }
	//agent { docker { image 'node:13.8'} }

    environment {
		dockerHome = tool 'myDocker'
		mavenHome = tool 'myMaven'
		PATH = "$dockerHome/bin:$mavenHome/bin:$PATH"
	}


	stages {
        stage ('Checkout') {
            steps {
                echo "=============================="
				echo "PATH - $PATH"
				echo "Build Number - $env.BUILD_NUMBER"
				echo "Build ID - $env.BUILD_ID"
				echo" Build Tag - $env.JOB_NAME"
				echo" Build Tag - $env.BUILD_TAG"
				echo" Build URL - $env.BUILD_URL"
				sh 'mvn --version'
				sh 'docker --version'
				//sh 'node --version'
				echo "========================================"
                
            }
		}
		stage ('Compile') {
			steps {
				sh "mvn clean compile"
			}
	            
        }
        // stage ('Test') {
        //     steps {
        //         sh "mvn test"
				
        //     }
            
        // }
		// stage ('Test Integration') {
        //     steps {
        //         //echo "Test Integration"

		// 		sh "mvn failsafe:integration-test failsafe:verify"
				
        //     }
            
        // }
		stage ('Package') {
			steps {
				sh "mvn package -DskipTests"
			}
		}	
		stage  ('Build Docker Image') {
          steps{
                 //docker build -t bkhbea/currency-exchange-devops:$env.BUILD_TAG
				 script {
					 dockerImage = docker.build("bkhbea/currency-exchange:${env.BUILD_TAG}")
				 }
		  }
		}
		stage  ('Push Docker Image') {
          steps{
                 script {
					 docker.withRegistry('','dockerHub') {
                     dockerImage.push();
				 }
		  }
		}

		
    }
    
  }
}


