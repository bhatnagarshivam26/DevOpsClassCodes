pipeline {
    agent any
    tools {
        maven 'mymaven'
        jdk 'java'
    }
    stages {
        stage ('Compile') {
            steps {
                sh 'mvn compile'
            }
        }

        stage ('CodeReview') {
            steps {
                sh 'mvn -Pmetrics pmd:pmd' 
            }
            post {
                success {
					pmd canComputeNew: false, defaultEncoding: '', healthy: '', pattern: 'target/pmd.xml', unHealthy: ''
                    
                }
            }
        }
		stage ('CodeReview') {
            steps {
                sh 'mvn test' 
            }
            post {
                success {
					junit 'target/surefire-reports/*.xml'
                    
                }
            }
        }
    }
}
