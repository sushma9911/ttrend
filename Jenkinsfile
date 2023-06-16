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
        stage('build'){0
            steps {
                echo '------------------- Build Started -------------'
                sh 'mvn clean deploy -Dmaven.test.skip=true'
                echo '------------------- Build Completed -------------'
            }
        }

    }

}

