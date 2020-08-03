pipeline{
        agent any
        stages {
            stage('Lint HTML'){
                steps {
                    sh 'tidy -q -e *.html'
                }
            }
            stage('Upload to AWS') {
                steps {
                    retry(3){
                        withAWS(region:'us-east-2c', credentials:'aws-static'){
                        s3Upload(file:'index.html', bucket:'jenkines-website', path:'/var/lib/jenkins/workspace/static_master/index.html')
                    }                             
                }
            }
        }
    }
}
