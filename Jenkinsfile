pipeline {
    agent any

    stages {

        stage('Build, Test & Package') {
            steps {
                sh 'mvn clean package'
            }
        }

        stage('Install to Local Repo') {
            steps {
                sh 'mvn install'
            }
        }
    }

    post {
        success {
            echo 'Library JAR packaged and installed successfully'
            archiveArtifacts artifacts: 'target/*.jar', fingerprint: true
        }
        failure {
            echo 'Build failed'
        }
    }
}
