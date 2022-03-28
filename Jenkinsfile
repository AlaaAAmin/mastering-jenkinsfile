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
            // u can control the execution of a stage using when expression
            when {
                expression {
                    // BRANCH_NAME is provided by jenkins and it tells u the active branch
                    // this expression will make this stage execute only if the branch is the feature branch
                    env.BRANCH_NAME == 'feature'
                }
            }
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
