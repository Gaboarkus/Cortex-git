pipeline {
  agent any
  environment {
      MAJOR = '1'
      MINOR = '0'
  }
  stages {
    stage ('Build') {
        UiPathAssets (
            assetsAction: DeployAssets(), 
            credentials: Token(accountName: '', credentialsId: ''), 
            filePath: '${WORKSPACE}/test.csv', 
            folderName: 'Default', 
            orchestratorAddress: 'https://test-orchestrator.somedomain.com', 
            orchestratorTenant: 'Default',
            traceLoggingLevel: 'None'
        )
        UiPathAssets(
            assetsAction: DeleteAssets(),
            credentials: UserPass('825c83c9-9a14-44eb-883a-af54f8078af0'),
            filePath: '${WORKSPACE}/test.csv',
            folderName: 'Default',
            orchestratorAddress: 'https://test-orchestrator.somedomain.com',
            orchestratorTenant: 'Default',
            traceLoggingLevel: 'None'
        )
  stages {
    stage ('PostBuild') {
      steps {
        UiPathTest (
          testTarget: [$class: 'TestSetEntry', testSet: "My Test Set"],
          orchestratorAddress: "OrchestratorUrl",
          orchestratorTenant: "tenant name",
          folderName: "folder name",
          timeout: "10000",
          traceLoggingLevel: 'None',
          testResultsOutputPath: "result.xml",
          credentials: [$class: 'UserPassAuthenticationEntry', credentialsId: "credentialsId"]
        )
    }
  }
}