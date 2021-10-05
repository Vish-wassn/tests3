pipeline {
    agent any

    stages{
        stage('deploy to S3'){
            steps{
                sh 'aws s3 cp public/index.html s3://s3demo30092021'
                sh 'aws s3api put-object-acl --bucket s3demo30092021 --key index.html --acl public-read'
               
            }
        }
    }
    post{
        always{
            cleanWs disableDeferredWipeout: true, deleteDirs: true
        }
    }

}
