pipeline {
    agent any

    stages {
        stage ('Compile Stage') {

            steps {
                withMaven(maven : 'maven_3_5_0') {
                    echo 'clean compile'
                }
            }
        }

        stage ('Testing Stage') {

            steps {
                withMaven(maven : 'maven_3_5_0') {
                    echo 'test'
                }
            }
        }


      
        stage ('Deploy Stage') {

            steps {
                withMaven(maven : 'maven_3_5_0') {
                    echo 'deploy'
                }
            }
        }
    }
}