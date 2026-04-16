pipeline {
    agent any

    stages {
        stage('Build Admin') {
            steps {
                dir('admin') {
                    echo 'Installing Admin Dependencies'
                    sh 'npm install --legacy-peer-deps'
                    
                    echo 'Building Admin Application'
                    sh 'npm run build'
                }
            }
        }
        
        stage('Build Frontend') {
            steps {
                dir('frontend') {
                    echo 'Installing Frontend Dependencies'
                    sh 'npm install --legacy-peer-deps'
                }
            }
        }
    }
    
    post {
        always {
            echo 'Pipeline execution complete'
        }
        success {
            echo 'Pipeline completed successfully!'
        }
        failure {
            echo 'Pipeline failed!'
        }
    }
}
