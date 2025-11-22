pipeline {
    agent none   // Runs on any available Jenkins agent

    stages {

        stage('Checkout') {
			agent {label 'slave2'}
            steps {
                echo "Checking out source code..."
                git(
                    url: 'https://github.com/akram194/java-build.git',
                    branch: 'master'
                )
            }
        }

        stage('Build') {
			agent {label 'slave2'}
            steps {
                echo "Building the application with Maven..."
                sh ''' 
				mvn clean package
				'''
            }
        }

        stage('Deploy') {
			agent {label 'slave1'}
            steps {
                echo "Deploying application..."
                // Example deploy step
                sh 'echo Deploying build artifact...'
                // You can replace with:
                // sh 'scp target/myapp.war user@server:/opt/tomcat/webapps/'
            }
        }

    }
}
