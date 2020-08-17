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
      cloudBeesFlowTriggerRelease configuration: 'flow-server', parameters: '{"release":{"releaseName":"qe release","stages":[{"stageName":"Stage 1","stageValue":""}],"pipelineName":"qe pipeline","parameters":[]}}', projectName: 'qe proj 1', releaseName: 'qe release', startingStage: 'Stage 1'
   }
   
}
