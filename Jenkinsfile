pipeline {
    agent any

    stages{
        stage('deploy to S3'){
            steps{
                sh 'aws s3 cp public/Readme.md s3://s3demo30092021'
                sh 'aws s3api put-object-acl --bucket s3demo30092021 --key Readme.md --acl public-read'
                sh 'aws s3 cp public/jenkinsfile s3://s3demo30092021'
                sh 'aws s3api put-object-acl --bucket s3demo30092021 --key jenkinsfile --acl public-read'
                sh 'aws s3 cp public s3://s3demo30092021 --recursive'
                sh 'aws s3api put-object-acl --bucket s3demo30092021 --key public --acl public-read'
                sh 'aws s3 cp public s3://s3demo30092021 --recursive'
                sh 'aws s3api put-object-acl --bucket s3demo30092021 --key .github_temp/workflows --acl public-read'
               
            }
        }
    }
    post{
        always{
            cleanWs disableDeferredWipeout: true, deleteDirs: true
        }
    }

}
