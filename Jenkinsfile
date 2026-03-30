pipeline {
    agent any 

    tools {
        // Ensure "Maven" matches the name in Jenkins Global Tool Configuration
        maven 'Maven-3.9.14' 
    }

    stages {
        stage('Checkout') {
            steps {
                // Pulls code from your configured SCM (Git)
                checkout scm
            }
        }

        stage('Build') {
            steps {
                echo 'Building the application...'
                // Compiles and packages the app while skipping tests for this stage
                sh 'mvn clean package -DskipTests'
            }
        }

        stage('Run Tests') {
            steps {
                echo 'Running unit tests...'
                // Executes JUnit tests
                sh 'mvn test'
            }
            post {
                always {
                    // Archives test results to display in the Jenkins UI
                    junit '**/target/surefire-reports/*.xml'
                }
            }
        }

        stage('Deploy') {
            steps {
                echo 'Deploying application...'
                // Replace with your actual deployment command (e.g., to Tomcat or S3)
                sh 'echo "Deployment step executed successfully"'
            }
        }
    }

    post {
        success {
            echo '✅ Pipeline finished successfully!'
        }
        failure {
            echo '❌ Pipeline failed.'
        }
    }
}
