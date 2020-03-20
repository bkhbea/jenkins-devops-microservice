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
        stage ('Build') {
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
        stage ('Test') {
            steps {
                echo "Test"
				
            }
            
        }
		stage ('Test Integration') {
            steps {
                echo "Test Integration"
				
            }
            
        }
    }
    post {
        always {
            
			echo "I always run - regardless - damn this actually works!!!" 
        }
		success {
            
			echo "I run when successful"
        }
        failure {
            
			echo "I run when I fail"
        }
		changed {
			echo "The status of this build is differnet than the last one"
		}

    }
}

