pipeline {
    agent {
        label 'base && nano'
    }
    
    stages {
        stage('Export features from Xray'){
            steps {
		git branch: 'xray_video', credentialsId: 'performgroup_jenkins_github_app', url: 'https://github.com/rpravipati/cucumber.git'
              }
        }
         
        stage('Test'){
            steps{
                sh "cd cucumber_xray_tests && cucumber -x -f json -o data.json"
            }
        }
         
        stage('Import results to Xray') {
            steps {
                step([$class: 'XrayImportBuilder', endpointName: '/cucumber', importFilePath: 'cucumber_xray_tests/data.json', serverInstance: '552d0cb6-6f8d-48ba-bbad-50e94f39b722'])
            }
        }
    }
}
