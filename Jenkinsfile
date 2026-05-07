pipeline {
    agent any

    stages {

        stage('Checkout') {
            steps {
                git branch: 'main',
                url: 'https://github.com/udaychittaluri1-sys/capstone-final.git'
            }
        }

        stage('Install Dependencies') {
            steps {
                bat 'pip install -r requirements.txt'
            }
        }

        stage('Run API Tests') {
            steps {
                bat 'pytest tests/api --html=reports/api_report.html'
            }
        }

        stage('Run UI Tests') {
            steps {
                bat 'pytest tests/ui --html=reports/ui_report.html'
            }
        }

        stage('Run E2E Tests') {
            steps {
                bat 'pytest tests/e2e --html=reports/e2e_report.html'
            }
        }

        stage('Run Regression Tests') {
            steps {
                bat 'pytest tests/regression --html=reports/regression_report.html'
            }
        }
    }

    post {
        always {
            archiveArtifacts artifacts: 'reports/*.html', fingerprint: true
        }
    }
}
