pipeline {
    agent any

    environment {
        PYTHON = "C:\\Users\\chitt\\AppData\\Local\\Programs\\Python\\Python311\\python.exe"
    }

    stages {

        stage('Checkout') {
            steps {
                git branch: 'main',
                url: 'https://github.com/udaychittaluri1-sys/capstone-final.git'
            }
        }

        stage('Install Dependencies') {
            steps {
                bat '"%PYTHON%" -m pip install --upgrade pip'
                bat '"%PYTHON%" -m pip install -r requirements.txt'
            }
        }

        stage('Run API Tests') {
            steps {
                bat '"%PYTHON%" -m pytest tests --html=reports/api_report.html'
            }
        }

        stage('Run UI Tests') {
            steps {
                bat '"%PYTHON%" -m pytest tests --html=reports/ui_report.html'
            }
        }

        stage('Run E2E Tests') {
            steps {
                bat '"%PYTHON%" -m pytest tests --html=reports/e2e_report.html'
            }
        }

        stage('Run Regression Tests') {
            steps {
                bat '"%PYTHON%" -m pytest tests --html=reports/regression_report.html'
            }
        }
    }

    post {
        always {
            archiveArtifacts artifacts: 'reports/*.html', fingerprint: true
        }
    }
}
