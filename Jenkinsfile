pipeline {
    agent any 
    stages {
        stage('Build') { 
            steps {
                println "Parameter1 value 1"
                println "commit 1"
                println "commit 2"
                println "commit 3"
                println "commit 4"
                println "commit 4"
                println "commit 5"
            }
        }
        stage('Test'){
            steps {
                echo 'Test step'
            }
        }
        stage('Deploy') {
            steps {
                echo 'Deploy step'
            }
        }
    }
    post {
        always {
            script {
                cloudBeesFlowRunPipeline addParam: '{"pipeline":{"pipelineName":"qe pipeline name","parameters":[]}}', configuration: 'flow-server', pipelineName: 'qe pipeline name', projectName: 'qe proj'
            }
        }
    }

}
