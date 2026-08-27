cd ~/devops-week5-demo

cat > Jenkinsfile << 'EOF'
pipeline {
    agent any
    stages {
        stage('Checkout') {
            steps {
                git branch: 'main', url: 'https://github.com/Oluwasola1/devops-week5-demo.git'
            }
        }
        stage('Build') {
            steps {
                echo 'Building application...'
                sh 'python3 --version'
            }
        }
        stage('Test') {
            steps {
                echo 'Running tests...'
                sh 'python3 app.py'
            }
        }
        stage('Validation') {
            steps {
                echo 'Running basic validation checks...'
                sh 'python3 -m py_compile app.py'
            }
        }
    }
    post {
        success {
            echo 'Pipeline succeeded!'
        }
        failure {
            echo 'Pipeline failed — check console output.'
        }
    }
}
EOF

git add Jenkinsfile
git commit -m "add validation stage"
git push
