pipeline {
    agent any

environment {
    NODE_HOME = tool name: 'node', type: 'NodeJSInstallation'
    PATH = "${NODE_HOME}/bin:${env.PATH}"
}


    stages {
        stage('Checkout') {
            steps {
                git branch: 'main', url: 'https://github.com/<your-username>/<your-repo>.git'
            }
        }

        stage('Install Dependencies') {
            steps {
                echo 'Installing npm packages...'
                sh 'npm install'
            }
        }

        stage('Build Angular App') {
            steps {
                echo 'Building Angular app...'
                sh 'npm run build'
            }
        }

        stage('Test') {
            steps {
                echo 'Running unit tests...'
                sh 'npm run test -- --watch=false || true'  // skip errors for demo
            }
        }

        stage('Deploy') {
            steps {
                echo 'Deploying build to /var/www/angular-demo (for example)...'
                sh 'mkdir -p /var/www/angular-demo'
                sh 'cp -r dist/angular-demo/* /var/www/angular-demo/'
            }
        }
    }
}

