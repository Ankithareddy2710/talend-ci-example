pipeline {
    agent any

    environment {
        JAVA_HOME = "C:\\Program Files\\Java\\jdk-21"
    }

    parameters {
        string(name: 'CSV_FILE_PATH', defaultValue: 'C:/Users/reddy/Downloads/customers (5).csv', description: 'Path to the CSV input file')
    }

    stages {
        stage('Checkout') {
            steps {
                git branch: 'main', url: 'https://github.com/Ankithareddy2710/talend-ci-example.git'
            }
        }

        stage('Run Talend Job') {
            steps {
                dir('CustomerLoggerJob') {
                    bat '''
                    call CustomerLoggerJob_run.bat --context=Default ^
                    --context_param CSV_FILE_PATH="%CSV_FILE_PATH%"
                    '''
                }
            }
        }
    }
}
