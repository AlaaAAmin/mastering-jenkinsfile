pipeline{
    agent any
    stages{
        stage('Build') {
            steps {
                //steps
                echo 'building the application...'
            }
        }
        stage('Test') {
            steps {
                //steps
                echo 'running tests on the application...'
            }
        }
        stage('Deploy') {
            steps {
                //steps
                echo 'deploying the application...'
            }
        }
    }
    // after the stages are completed we can define post actions
    post {
        always {
            // executes everytime a build has finished
        }
        success {
            //executes upon successful build
        }
        failure {
            // executes upon build failure
        }
    }
}