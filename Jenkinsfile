//node ('maven') {
//    checkout scm
//    sh 'mvn -Dmaven.test.failure.ignore=true test'
//    step([$class: 'JUnitResultArchiver', testResults: '**/target/surefire-reports/TEST-*.xml'])
//}

node {
    stage('BuildS2I') {
        openshiftBuild apiURL: '', authToken: '', bldCfg: 's2i-java', buildName: '', checkForTriggeredDeployments: 'false', commitID: '', namespace: 'bosse-demo-builder', showBuildLogs: 'true', verbose: 'false', waitTime: '', waitUnit: 'sec'
        openshiftVerifyBuild apiURL: '', authToken: '', bldCfg: 's2i-java', checkForTriggeredDeployments: 'false', namespace: 'bosse-demo-builder', verbose: 'false', waitTime: ''
    }
    
    stage('BuildApp') {
        openshiftBuild apiURL: '', authToken: '', bldCfg: 's2i-app', buildName: '', checkForTriggeredDeployments: 'true', commitID: '', namespace: 'bosse-demo-dev', showBuildLogs: 'true', waitTime: '', waitUnit: 'sec'
        openshiftDeploy apiURL: '', authToken: '', depCfg: 's2i-app', namespace: 'bosse-demo-dev', verbose: 'false', waitTime: '', waitUnit: 'sec'
    }
}
