pipeline {
    agent {
        node {
            label 'mavenagent'
        }
    }

environment {
    PATH = "/opt/apache-maven-3.9.2/bin:$PATH"
}
    stages {
        stage('build'){
            steps {
                echo '------------------- Build Started -------------'
                sh 'mvn clean deploy -Dmaven.test.skip=true'
                echo '------------------- Build Completed -------------'
            }
        }

	stage('Unit Test') {
            steps{
                echo '------------------- Unit Test Started -------------'
                sh 'mvn surefire-report:report'
                echo '------------------- Unit Test Completed -------------'
            }
        }
	    

	stage('SonarQube analysis') {
            environment {
            scannerHome = tool 'sonarscanner'
            }
        steps {
            echo '------------------- Sonar Started -------------'
        withSonarQubeEnv('sonarqube-server') { // If you have configured more than one global server connection, you can specify its name
            sh "${scannerHome}/bin/sonar-scanner"
    }
    echo '------------------- Sonar Analysis Completed -------------'
  }
}

    }

}

