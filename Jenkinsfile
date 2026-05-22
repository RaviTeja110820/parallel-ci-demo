pipeline {

    agent any
    // Run the pipeline on any available Jenkins agent

    tools {
        maven 'mymaven'
        // Uses the Maven version configured in Jenkins (Manage Jenkins → Tools)
    }

    stages {

        stage('Checkout') {
            steps {
                // Clone the Git repository
                git branch: 'main', \
                    url: 'https://github.com/RaviTeja110820/Implementing-Parallel-CI-Pipeline-in-Jenkins.git'
            }
        }

        stage('Build') {
            steps {
                sh 'mvn clean compile'
            }
        }

        stage('Parallel Tests') {
            parallel {

                stage('Unit Tests') {
                    steps {
                        // Run unit tests
                        sh 'mvn test'
                    }
                }

                stage('Integration Tests') {
                    steps {
                        // Run integration tests
                        sh 'mvn verify'
                    }
                }

                stage('Code Analysis') {
                    steps {
                        // Static code analysis using PMD
                        sh 'mvn pmd:pmd'
                    }
                }

                
            }
        }
    }
}