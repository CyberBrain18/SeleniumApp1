pipeline {
    agent any

    tools {
        jdk 'JDK'
        maven 'Maven'
    }

    stages {
        stage('Checkout') {
            steps {
                git branch: 'master', url: 'https://github.com/CyberBrain18/SeleniumApp1.git'
            }
        }

        stage('Build & Compile') {
            steps {
                // Ensure dependencies are downloaded and code is compiled
                sh 'mvn clean compile'
            }
        }

        stage('Selenium UI Tests') {
            steps {
                // Running tests. 
                // We use -DskipTests=false to ensure Maven runs them.
                sh 'mvn test'
            }
        }
    }

    post {
        always {
            // This pulls the test results into the Jenkins UI
            junit '**/target/surefire-reports/*.xml'
        }
        success {
            echo 'Selenium Automation Passed Successfully!'
        }
    }
}
