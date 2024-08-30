pipeline {
    agent any
    stages {
        stage('Build') {
            steps {
                echo 'Building...'
                sh 'mvn clean package'
            }
        }
        stage('Unit and Integration Tests') {
            steps {
                echo 'Running unit and integration tests...'
                sh 'mvn test'
            }
        }
        stage('Code Analysis') {
            steps {
                echo 'Analyzing code with Checkstyle...'
                sh 'mvn checkstyle:check'
            }
        }
        stage('Security Scan') {
            steps {
                echo 'Running security scan...'
            }
        }
        stage('Deploy to Staging') {
            steps {
                echo 'Deploying to staging...'
            }
        }
        stage('Integration Tests on Staging') {
            steps {
                echo 'Running integration tests on staging...'
            }
        }
        stage('Deploy to Production') {
            steps {
                echo 'Deploying to production...'
            }
        }
    }
    post {
        always {
            echo 'Pipeline finished'
        }
        success {
            emailext (
                subject: "Build Success: ${currentBuild.fullDisplayName}",
                body: "Good news, ${currentBuild.fullDisplayName} succeeded.",
                to: 'y0435199268@gmail.com',
                from: 'y0435199268@gmail.com',
                attachLog: true
            )
        }
        failure {
            emailext (
                subject: "Build Failed: ${currentBuild.fullDisplayName}",
                body: "Something went wrong, ${currentBuild.fullDisplayName} failed.",
                to: 'y0435199268@gmail.com',
                from: 'y0435199268@gmail.com',
                attachLog: true
            )
        }
    }
}

