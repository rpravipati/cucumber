pipeline {
    agent {
        label 'base && nano'
    }
    parameters {
        string(name: 'TEST_KEY', defaultValue: 'DVOC-1552', description: 'test')
        choice(name: 'STATUS', choices: ['Pass', 'Fail'], description: 'Pick status')
    }
    stages {
        stage('Export features from Xray'){
            steps {
		git branch: 'xray_video', credentialsId: 'performgroup_jenkins_github_app', url: 'https://github.com/rpravipati/cucumber.git'
              }
        }
         
        stage('Import results to Xray') {
            steps {
                step([$class: 'XrayImportBuilder', endpointName: '', importFilePath: '/cucumber/result.xml', importInParallel: 'false', serverInstance: 'CLOUD-2a367cdf-a677-4299-a0be-ae5b08926dc8'])
            }
        }
    }
}
