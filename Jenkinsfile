pipeline{
    agent {
        dockerfile {
            filename 'Dockerfile'
            args '-v /.cache/ -v /.bower/  -v /.config/configstore/'
        }
    }

    stages{
        stage('starting application'){
            steps{
                sh 'npm install'
            }
        }
    }
}