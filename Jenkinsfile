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
	    environment {
		IMG_NAME='iszilasi/helloworld'
	    }
            steps { 
	        git url: 'https://github.com/iszilasi/helloworld.git'
                sh 'echo "Build: " ${BUILD_NUMBER}'
		sh 'echo ${IMG_NAME}'
		withCredentials([usernamePassword(credentialsId: 'iszilasi_dh1', usernameVariable: 'DH_USER', passwordVariable: 'DH_PASSWORD')]) { sh 'docker login -u $DH_USER -p $DH_PASSWORD' }
		sh 'docker build . -t ${IMG_NAME}:${BUILD_NUMBER}'
		sh 'docker push ${IMG_NAME}:${BUILD_NUMBER}'
            }
        }
    }
    post {
    	success {
		build job: 'Run test on project', parameters: [ [$class: 'StringParameterValue', name: 'IMAGENAME_TAG', value: IMG_NAME + ":" + BUILD_NUMBER ]]
	}
    }
}
