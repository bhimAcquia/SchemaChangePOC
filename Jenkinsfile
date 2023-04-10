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
                sh "schemachange -f snowflake/common -a ${SF_ACCOUNT} -u ${SF_USERNAME} -r ${SF_ROLE} -w ${SF_WAREHOUSE} -d ${SF_DATABASE} -c ${SF_DATABASE}.SCHEMACHANGE.CHANGE_HISTORY_COMMON --create-change-history-table"
                sh "schemachange -f snowflake/tenants/tenant_803 -a ${SF_ACCOUNT} -u ${SF_USERNAME} -r ${SF_ROLE} -w ${SF_WAREHOUSE} -d ${SF_DATABASE} -c ${SF_DATABASE}.SCHEMACHANGE.CHANGE_HISTORY_COMMON --create-change-history-table"
            }
        }
    }
}