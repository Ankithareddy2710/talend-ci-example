pipeline {
    agent any

    environment {
        JAVA_HOME = "C:\\Program Files\\Java\\jdk-21"
        CSV_PATH = 'C:/Users/reddy/Downloads/customers (5).csv'
    }

    parameters {
        string(name: 'CSV_FILE_PATH', defaultValue: "${CSV_PATH}", description: 'Path to the CSV input file')
    }

    stages {
        stage('Checkout') {
            steps {
                // Clones the full talend_projects structure
                git branch: 'main', url: 'https://github.com/Ankithareddy2710/talend-ci-example.git'
            }
        }

        stage('Run Talend Job') {
            steps {
                dir('CustomerLoggerJob') {
                    bat """
                        call CustomerLoggerJob_run.bat --context=Default ^
                        --context_param CSV_FILE_PATH="${params.CSV_FILE_PATH}"
                    """
                }
            }
        }
    }
}
