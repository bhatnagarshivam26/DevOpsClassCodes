pipeline {
    agent any
        tools {
            maven 'mymaven'
            jdk 'java'
            }
    stages {
        stage ('compile') {
            steps {
                sh 'mvn compile'
            }
        }
    }
}
