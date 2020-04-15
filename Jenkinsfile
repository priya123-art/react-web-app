pipeline{
 agent any
  
  tools {
  nodejs 'node'
  }
  
  stages{
    stage('Build'){
      steps{
        script
            {
         cleanWs()
         checkout([$class: 'GitSCM', branches: [[name: '*${RepoBranch}']], doGenerateSubmoduleConfigurations: false, extensions: [], submoduleCfg: [], userRemoteConfigs: [[credentialsId: 'priya123-art', url: 'https://github.com/priya123-art/react-web-app.git']]])
         sh '''
         ls -ltr
         npm install
         npm run build
         ls -ltr
         cd build/
              ls -ltr
         '''
             
           }
      
         }
    
           }
  }
  
}
