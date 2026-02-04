pipeline {
    agent any
    
    stages {
        stage('Clone') {
            steps {
                echo 'Cloning code from Git...'
            }
        }
        stage('Build') {
            steps {
                echo 'Building project...'
                bat 'echo "Build step executed"'
            }
        }
        stage('Test') {
            steps {
                echo 'Running tests...'
                bat 'echo "Tests passed"'
            }
        }
    }
    
    post {
        success {
            echo '✅ PIPELINE SUCCESS: All stages completed successfully!'
        }
        failure {
            echo '❌ PIPELINE FAILED: Check the logs for errors.'
        }
        always {
            echo '📦 Pipeline execution completed.'
        }
    }
}
