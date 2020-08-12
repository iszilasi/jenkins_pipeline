pipeline { 
    agent none
    options {
        skipStagesAfterUnstable()
    }
    stages {
        stage('Build') {
	    agent {
	       label {'!static'}
	    }
            steps { 
                sh 'cat README' 
            }
        }
        stage('Test'){
            steps {
                sh 'echo "test"'
            }
        }
    }
}
