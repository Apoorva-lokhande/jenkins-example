pipeline {
    agent any

    stages {
        stage ('Compile Stage') {

            steps {
                withMaven(maven : 'maven_3_5_0') {
                    sh 'mvn clean compile'
                }
            }
        }

        stage ('Testing Stage') {

            steps {
                withMaven(maven : 'maven_3_5_0') {
                    sh 'mvn test'
                }
            }
        }


       stage ('NodeJsScan Analysis') {
            steps {
                sh 'nodejsscan --directory `pwd` --output /reports/nodejsscan-report'
            }
        }
    }
}