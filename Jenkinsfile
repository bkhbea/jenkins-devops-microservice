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
    //agent any
    //agent { docker { image 'maven:3.6.3'} }
	agent { docker { image 'node:13.8'} }
	stages {
        stage ('Build') {
            steps {
                echo "=============================="
				//sh 'mvn --version'
				sh 'node --version'
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

    }
}

