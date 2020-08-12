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
                sh 'echo "Build: " ${BUILD_NUMBER}'
		sh 'export IMG_NAME="iszilasi/helloworld:${BUILD_NUMBER}"'
		sh 'echo ${IMG_NAME}'
		withCredentials([usernamePassword(credentialsId: 'iszilasi_dh1', usernameVariable: 'DH_USER', passwordVariable: 'DH_PASSWORD')]) { sh 'docker login -u $DH_USER -p $DH_PASSWORD' }
		sh 'docker build . -t ${IMG_NAME}'
		sh 'docker push ${IMG_NAME}'
            }
        }
        stage('Test'){
            steps {
                echo "test"
            }
        }
    }
}
