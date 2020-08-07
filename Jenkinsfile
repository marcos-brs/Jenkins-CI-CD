pipeline {
    agent any
    stages {
        stage('Lint HTML') {
            steps {
                sh 'tidy -q -e *.html'
            }
        }
        stage('Upload to AWS') {
            steps {
                retry(3) {
                        withAWS(region:'us-west-2', credentials:'aws-static') {
                            s3Upload(file:'index.html', bucket:'jenkins-s3-bucket-ud', path:'')
                    }  
                }     
            }
        }
    }
}