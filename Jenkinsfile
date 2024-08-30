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
                echo 'Analyzing code...'
                withEnv(["PATH+SONAR=/opt/homebrew/bin:/usr/bin:/bin:/opt/homebrew/opt/maven/bin"]) {
                    sh 'sonar-scanner -Dsonar.projectKey=your_project_key -Dsonar.organization=your_organization -Dsonar.login=$SONAR_TOKEN'
                }
            }
        }
        stage('Security Scan') {
            steps {
                echo 'Running security scan...'
                // 在这里配置你选择的安全扫描工具
            }
        }
        stage('Deploy to Staging') {
            steps {
                echo 'Deploying to staging...'
                // 在这里配置部署脚本
            }
        }
        stage('Integration Tests on Staging') {
            steps {
                echo 'Running integration tests on staging...'
                // 在这里配置集成测试脚本
            }
        }
        stage('Deploy to Production') {
            steps {
                echo 'Deploying to production...'
                // 在这里配置部署到生产环境的脚本
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
                attachLog: true
            )
        }
        failure {
            emailext (
                subject: "Build Failed: ${currentBuild.fullDisplayName}",
                body: "Something went wrong, ${currentBuild.fullDisplayName} failed.",
                to: 'y0435199268@gmail.com',
                attachLog: true
            )
        }
    }
}

