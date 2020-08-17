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
       cloudBeesFlowAssociateBuildToRelease configuration: 'flow-server', flowRuntimeId: '7d85ccd5-e08e-11ea-86ae-42010a00000d', projectName: 'qe proj 1', releaseName: 'qe release'
   }
   
}
