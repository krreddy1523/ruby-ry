pipeline{
    agent any
    stages{
     
     stage('copying files'){
         
         steps{
             sh '''
              
              #!/bin/bash
              
              #ssh deployer-azure ' scp /home/ubuntu/config/*.yml scaleset_ls_3:/u/apps/live_status/shared/config '
            
      '''        
         }
         
     }
     
    stage (' Process to depolying '){
        
             steps {
                 
                 sh '''
                 
                 # ssh deployer-azure ' cd /u/apps/railyatri.live_status_5 && eval $(ssh-agent) && ssh-add && source ~/.rvm/scripts/rvm && cd /u/apps/railyatri.live_status_5 && cap production_ss3 deploy '
                  
                  ssh scaleset_ls_4 ' cd /u/apps/live_status/current  && cap production_1 deploy '
                  
                  '''
                 
             }
        
    }
    
     stage (deploy){
         
         steps {
             
             sh """
             
        #     ssh deployer-azure ' cd /u/apps/railyatri.live_status_5 && cap production_ss3 deploy'
                  
                  ssh scaleset_ls_4 ' curl localhost/api/home.json?[1-10] '
                  
                  """
         }
         
     }
     
     stage ('mail') {
         
         steps{
             
             emailext body: 'live status deploy', subject: 'build is success', to: 'rajasekhar.reddy@railyatri.in'
             
         }
         
     }
     
        
    }
    
}
