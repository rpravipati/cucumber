pipeline {
    agent {
        label 'base && nano'
    }
    parameters {
        string(name: 'TEST_KEY', defaultValue: 'DVOC-1552', description: 'test')
        choice(name: 'STATUS', choices: ['Pass', 'Fail'], description: 'Pick status')
	string(defaultValue: "DEV", description: '', name: 'ENV') 
    }

    stages {
        stage ('Import Results') {
            steps {
                step([$class: 'XrayImportBuilder',
                endpointName: '',
                importFilePath: '/cucumber/result.xml',
                importToSameExecution: 'true',
                projectKey: params.TEST_KEY,
                revision: params.TEST_KEY + env.BUILD_NUMBER,
                serverInstance: 'CLOUD-2a367cdf-a677-4299-a0be-ae5b08926dc8',
                testEnvironments: params.ENV])
            }
             
        }
    }
}
