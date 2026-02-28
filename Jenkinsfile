pipeline {
    agent any

    stages {

        stage('Build, Test & Package') {
            steps {
                dir('demo') {
                    sh 'mvn clean package'
                }
            }
        }

        stage('Install to Local Repo') {
            steps {
                dir('demo') {
                    sh 'mvn install'
                }
            }
        }
    }

    post {
        success {
            echo 'Library JAR packaged and installed successfully'
            archiveArtifacts artifacts: 'demo/target/*.jar', fingerprint: true
        }
        failure {
            echo 'Build failed'
        }
    }
}
