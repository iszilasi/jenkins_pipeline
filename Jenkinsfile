pipeline { 
    agent !static 
    options {
        skipStagesAfterUnstable()
    }
    stages {
        stage('Build') { 
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
