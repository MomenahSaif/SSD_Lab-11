pipeline {
    agent any
    tools {
        maven 'Maven'
    }
    parameters{

            string(name: 'VERSION',defaultValue:'',description:'version to deploy on prod')
            choice (name: 'VERSION',choices:['1.1.0','1.2.0','1.3.0'],description:'')
            booleanParam(name:'executeTests',defaultValue:true,description:'')


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
            when{
                    expression{
                                params.executeTests
                                }
                }
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
