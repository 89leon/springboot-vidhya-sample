pipeline {
    agent any

    stages {
        stage('Build') {
            steps {
                echo 'Building..'
                withMaven(maven : 'maven3_6_3'){
                    sh 'mvn --version'
                }
            }
        }

    }
}