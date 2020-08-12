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
                cat README 
            }
        }
        stage('Test'){
            steps {
                echo "test"
            }
        }
    }
}
