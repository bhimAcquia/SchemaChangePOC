pipeline {
    agent { 
        docker { 
            image "python:3.8"
            args '--user 0:0'
        } 

    }
    stages {
        stage('Run schemachange') {
            steps {
                sh "pip install schemachange --upgrade"
                sh "snowchange deploy --include common,tenants/tenant_803 -config-folder snowflake"
            }
        }
    }
}