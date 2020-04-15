pipeline{
 agent any
  
  tools {
  nodejs 'node'
  }
  
  stages{
    stage('Build'){
      steps{
        script{
         checkout([$class: 'GitSCM', branches: [[name: '*${RepoBranch}']], doGenerateSubmoduleConfigurations: false, extensions: [], submoduleCfg: [], userRemoteConfigs: [[credentialsId: 'priya123-art', url: 'https://github.com/priya123-art/react-web-app.git']]])
        }
      
      }
    
    }
  }
  
}
