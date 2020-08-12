pipeline { 
    agent none
    options {
        skipStagesAfterUnstable()
    }
    stages {
        stage('Build') {
	    agent {
	       label '!static'
	    }
            steps { 
	        git url: 'https://github.com/iszilasi/helloworld.git'
                sh 'ls' 
            }
        }
        stage('Test'){
            steps {
                echo "test"
            }
        }
    }
}
