pipeline {
    agent any

    environment {
        // Default value (can be overridden)
        ENABLE_FEATURE_X = 'false'
    }

    stages {
        stage('Setup Feature Flags') {
            steps {
                script {
                    // Example: Enable feature if branch name starts with feature/enable-x
                    if (env.BRANCH_NAME.startsWith('feature/enable-x')) {
                        env.ENABLE_FEATURE_X = 'true'
                        echo "Feature X Enabled"
                    } else {
                        env.ENABLE_FEATURE_X = 'false'
                        echo "Feature X Disabled"
                    }
                }
            }
        }

        stage('Build') {
            steps {
                echo "Building on branch: ${env.BRANCH_NAME}"
                echo "Feature X is enabled: ${env.ENABLE_FEATURE_X}"
                // Your build steps here
            }
        }

        stage('Deploy') {
            when {
                expression { return env.ENABLE_FEATURE_X == 'true' }
            }
            steps {
                echo "Deploying Feature X"
                // Deploy with feature X enabled
            }
        }
        stage('Check Commit Message') {
    steps {
        script {
            def commitMsg = sh(returnStdout: true, script: 'git log -1 --pretty=%B').trim()
            if (commitMsg.contains('[enable-feature-x]')) {
                env.ENABLE_FEATURE_X = 'true'
            } else {
                env.ENABLE_FEATURE_X = 'false'
            }
            echo "Feature X flag from commit message: ${env.ENABLE_FEATURE_X}"
        }
    }
}

    }
}
