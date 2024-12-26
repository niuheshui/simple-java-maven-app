

pipeline {
    agent any

    options {
	skipStagesAfterUnstable()
    }

    stages {
        stage('构建') { 
            steps {
                sh 'mvn -B -DskipTests clean package' 
            }
	    post {
	    	always {
		    sh 'echo Build stage is over'	
		}
	    }
        }

	stage('测试') {
	    steps {
	    	sh 'mvn test'
	    }
	    post {
	    	always {
		    junit 'target/surefire-reports/*.xml'
		}
	    }
	}

	stage('Deliver') {
	    steps {
	        sh './jenkins/scripts/deliver.sh'
	    }
	}



    }
}


