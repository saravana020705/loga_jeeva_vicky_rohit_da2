pipeline {
    agent any
    
    triggers {
        pollSCM('* * * * *')
    }
    
    stages {
        stage('Checkout') {
            steps {
                echo 'Checking out code from Git...'
                checkout scm
            }
        }
        
        stage('Compile') {
            steps {
                echo 'Compiling code...'
                bat 'javac HelloWorld.java'
            }
        }
        
        stage('Archive Artifacts') {
            steps {
                echo 'Archiving build artifacts...'
                bat 'echo "Build Success" > build-artifact.txt'
                archiveArtifacts artifacts: 'build-artifact.txt', fingerprint: true
            }
        }
    }
    
    post {
        success {
            echo '✅ CI Pipeline succeeded! Artifacts archived.'
        }
        failure {
            echo '❌ CI Pipeline failed! Check logs.'
        }
    }
}
