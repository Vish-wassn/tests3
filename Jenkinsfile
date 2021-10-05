pipeline {
    agent any

    stages{
        stage('deploy to S3'){
            steps{
                sh 'aws s3 cp public/package-lock.json s3://s3demo30092021'
                sh 'aws s3api put-object-acl --bucket s3demo30092021 --key package-lock.json --acl public-read'
                sh 'aws s3 cp public/package.json s3://s3demo30092021'
                sh 'aws s3api put-object-acl --bucket s3demo30092021 --key package.json --acl public-read'
                  
            }
        }
    }
    post{
        always{
            cleanWs disableDeferredWipeout: true, deleteDirs: true
        }
    }

}
