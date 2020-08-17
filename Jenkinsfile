node {
   def mvnHome
   stage('Build') {
      cleanWs()
      git 'https://github.com/masyaka2018/qatestrepo.git'
      mvnHome = tool 'mvn'
      withEnv(["MVN_HOME=$mvnHome"]) {
          sh '"$MVN_HOME/bin/mvn" install'
      }
   }
   stage('Test') {
       archiveArtifacts 'target/*.jar'
       junit 'target/surefire-reports/*.xml'
   }   
	
   stage('PBA'){
      cloudBeesFlowRunPipeline addParam: '{"pipeline":{"pipelineName":"qe pipeline","parameters":[]}}', configuration: 'flow-server', pipelineName: 'qe pipeline', projectName: 'qe proj'
   }
   
}
