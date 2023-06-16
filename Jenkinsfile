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

	stage('SonarQube analysis') {
            environment {
            scannerHome = tool 'sonarqube-server'
            }
        steps {
            echo '------------------- Sonar Started -------------'
        withSonarQubeEnv('sonarqube-scanner') { // If you have configured more than one global server connection, you can specify its name
            sh "${scannerHome}/bin/sonar-scanner"
    }
    echo '------------------- Sonar Analysis Completed -------------'
  }
    }

    }

}

