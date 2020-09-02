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
  stage('Publish'){
	cloudBeesFlowPublishArtifact artifactName: 'com.demo:helloworld', artifactVersion: '${BUILD_NUMBER}-SNAPSHOT', configuration: 'flow-server', filePath: 'target/helloworld-1.0-SNAPSHOT.jar', repositoryName: 'default'
   }
	
   stage('PBA'){
      cloudBeesFlowRunPipeline addParam: '{"pipeline":{"pipelineName":"qe pipeline name","parameters":[]}}', configuration: 'flow-server', pipelineName: 'qe pipeline name', projectName: 'qe proj'
   }
   stage('test'){
           echo 'test1'
	   echo 'test2'
	   echo 'test3'
   }
}
