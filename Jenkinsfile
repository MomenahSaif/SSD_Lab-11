pipeline {
    agent any
    tools {
        maven 'Maven'
    }
    environment {
        NEW_VERSION = '1.3.0'
    }
    stages {
        stage('Build') {
            steps {
                echo 'Building..'
                echo "Building version ${NEW_VERSION}"
                sh '''
                    # Source nvm manually
                    export NVM_DIR="$HOME/.nvm"
                    [ -s "$NVM_DIR/nvm.sh" ] && . "$NVM_DIR/nvm.sh"  # This loads nvm
                    nvm install node
                '''
            }
        }
        stage('Test') {
            steps {
                echo 'Testing..'
            }
        }
        stage('Deploy') {
            steps {
                echo 'Deploying....'
            }
        }
    }
    post {
        always {
            echo 'Post build condition running'
        }
        failure {
            echo 'Post Action if Build Failed'
        }
    }
}
