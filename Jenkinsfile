pipeline {
    agent any

    environment {
        JAVA_HOME = 'C:\\Program Files\\Java\\jdk-21'
    }

    parameters {
        string(name: 'CSV_FILE_PATH', defaultValue: 'C:/Users/reddy/Downloads/customers.csv', description: 'CSV input path')
    }

    stages {
        stage('Checkout') {
            steps {
                git url: 'https://github.com/Ankithareddy2710/talend-ci-cdc-job.git', branch: 'main'
            }
        }

        stage('Run Talend Job') {
            steps {
                dir('CDC_HashBased_Customers_WithJoblet') {
                    bat '''
                    call CDC_HashBased_Customers_WithJoblet_run.bat --context=Default ^
                    --context_param CSV_FILE_PATH="%CSV_FILE_PATH%"
                    '''
                }
            }
        }
    }
}
