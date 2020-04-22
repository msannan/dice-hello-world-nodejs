pipeline 
{
    agent any
    environment 
    {
      registryCredential = 'dockerhub' 
    }
    
    stages 
    {
        stage('Build') 
        {
            steps 
            {
              sh 'docker build -t sannan1357/test-node-app .'
            }
        }
        
        stage('Test')
        {
            steps 
            {
              sh 'docker container run -p 8001:8080 --name node -d sannan1357/test-node-app' 
              sh 'curl -I http://localhost:8001'
            }
         }
         
       stage('Publish') 
        {
             steps{
               script 
               {
                  docker.withRegistry( '', registryCredential ) 
                  {
                sh 'docker push sannan1357/test-node-app:latest' }
                  }
               }
         }
    }
}
