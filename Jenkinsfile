pipeline {
    agent any
    
    triggers {
        pollSCM('* * * * *')  // Poll Git every minute (for demo)
        // Or use webhook: githubPush() if you set up webhook
    }
    
    stages {
        stage('Checkout') {
            steps {
                echo 'Checking out code from Git...'
                checkout scm  // This clones your repo
            }
        }
        
        stage('Compile') {
            steps {
                echo 'Compiling code...'
                bat '''
                    echo Simulating compilation...
                    javac HelloWorld.java 2> compile.log
                    type compile.log
                '''
            }
            post {
                failure {
                    echo '❌ Compilation failed!'
                    error('Build failed due to compilation error')
                }
            }
        }
        
        stage('Archive Artifacts') {
            steps {
                echo 'Archiving build artifacts...'
                bat 'echo Creating demo artifact... && echo "Build Success" > build-artifact.txt'
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
