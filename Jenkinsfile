pipeline {

    agent {
	label 'appengine'
    }

    stages {
	
	stage('Git Checkout') {
	    steps {
		echo 'Pulling...' + env.BRANCH_NAME
		checkout scm
	    }
	}	
	

        stage('Build') {
	    steps {
                sh 'mvn -B -DskipTests clean package'
            }
        }


        stage('Test') {
            steps {
                sh 'mvn test'
            }
            post {
                always {
                    junit 'target/surefire-reports/*.xml'
                }
            }
        }
    }
}
