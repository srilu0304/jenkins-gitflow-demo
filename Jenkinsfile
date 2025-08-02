pipeline {
    agent any

    stages {
        stage('Build') {
            steps {
                echo "Building branch: ${env.BRANCH_NAME}"
                // Dummy build step
            }
        }

        stage('Test') {
            steps {
                echo "Running tests on branch: ${env.BRANCH_NAME}"
                // Dummy test step
            }
        }

        stage('Deploy') {
            when {
                anyOf {
                    branch 'master'
                    buildingTag()
                }
            }
            steps {
                echo "Deploying branch: ${env.BRANCH_NAME}"
                // Dummy deploy step
            }
        }
    }
    post {
        always {
            echo "Pipeline finished for branch: ${env.BRANCH_NAME}"
        }
    }
}
