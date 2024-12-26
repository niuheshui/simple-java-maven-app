

pipeline {
    agent any
    stages {
        stage('Build') { 
            steps {
                sh 'mvn -B -DskipTests clean package' 
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
    }
}


