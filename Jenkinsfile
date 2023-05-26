pipeline {
    agent any
    parameters {
        string(name: 'STRING', defaultValue: 'string default', description: 'Enter the STRING value')

        text(name: 'TEXT', defaultValue: '', description: 'Enter the TEXT value')

        booleanParam(name: 'BOOLEAN', defaultValue: true, description: 'Select the BOOLEAN value')

        choice(name: 'CHOICE', choices: ['One', 'Two', 'Three'], description: 'Select the CHOICE value')

        password(name: 'PASSWORD', defaultValue: 'SECRET', description: 'Enter the PASSWORDvalue')
    }
    stages {
        stage('Values') {
            steps {
                echo "STRING ${params.STRING}"

                echo "TEXT: ${params.TEXT}"

                echo "BOOLEAN: ${params.BOOLEAN}"

                echo "CHOICE: ${params.CHOICE}"

                echo "Password: ${params.PASSWORD}"
            }
        }
    }
}