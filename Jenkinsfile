// you can define global variables here
// def varName

pipeline{
    agent any
    parameters {
        // params syntax is type(name: 'paramName', defaultValue: '' or choices['',''], description: '')
        // can be accessed in the jenkinsfile using ${params.paramName}
        booleanParam(name: 'executeTests', defaultValue: true, description: 'controls the execution of tests')
        choice(name: 'exampleChoice', choices: ['#1', '#2', '#3'], description: 'some random choices')
        string(name: 'version', defaultValue: 'latest', description: 'the build version')
    }
    tools {
        // tools specifies the plugins used for building, testing, deploying, ...etc
        // syntax: tool-name 'tool installation name in jenkins'
        maven "M3"
    }
    //defining environmental variables
    environment {
        // NEW_VERSION is an env variable
        NEW_VERSION = '1.1.0'
        // to get credentials previously defined in jenkins itself we need make use of credentials("credId")
        // and we need the credentials binding plugin installed in jenkins
        ARTIFACTORY_SERVER_CREDENTIALS = credentials('artifactory-credits')
    }
    stages{
        stage('Init') {
            steps {
                echo 'initializing external scripts...'
                // script {
                    // the syntax to do so is:
                    // varName = load "path of the file"
                    // NOTE: to be able to access the varName through the file u need to define it
                    // as a global above the pipeline
                // }
            }
        }
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
                    env.BRANCH_NAME == 'feature' || params.executeTests
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
            echo 'new build...'
            echo "build version ${params.version} has been built"
        }
        success {
            //executes upon successful build
            echo 'build successeded...'
            echo "build version ${params.version} has been built"
            echo "artifactory credits ${ARTIFACTORY_SERVER_CREDENTIALS}"
        }
        failure {
            // executes upon build failure
            echo'build failed...'
            echo "build version ${params.version} have failed"
        }
    }
}
