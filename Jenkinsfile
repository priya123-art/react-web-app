pipeline
{
 agent any
  
 tools
  {
    nodejs 'node' 
    
  }

 stages
  {
   stage('Build')
    {
     steps
      {
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
         tar -cvf frontend-${BUILD_NUMBER}.tar *
         cp frontend-${BUILD_NUMBER}.tar ${WORKSPACE}/
         ls -ltr
         '''
          
        
        }
      }
     
    }
  stage('Deploy')
   {
    steps
    {
     sh '''
     rm -rf deploy
     mkdir deploy
     cp -r frontend-${BUILD_NUMBER}.tar deploy/
     cd deploy
     tar -xvf frontend-${BUILD_NUMBER}.tar
     rm -rf frontend-${BUILD_NUMBER}.tar
     ls -ltr
     gsutil acl ch -u AllUsers:R gs://priya-srivastava
     gsutil defacl set public-read gs://priya-srivastava
     gsutil web set -m index.html -e index.html gs://priya-srivastava
     
     gsutil cp -r * gs://priya-srivastava
     gsutil setmeta -h "content-type: image/svg+xml" gs://priya-srivastava/static/media/*.svg
     
      '''
    } 
      }
     
    }  
    
  
}  
