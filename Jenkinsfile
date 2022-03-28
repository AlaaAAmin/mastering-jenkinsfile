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
            echo 'always notify me of new builds...'
        }
        success {
            //executes upon successful build
            echo'notify me on success...'
        }
        failure {
            // executes upon build failure
            echo'notify me on failures...'
        }
    }
}
