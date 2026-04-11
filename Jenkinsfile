pipeline {
        agent {
            node {
            label 'repo3'
            customWorkspace "/mnt/node"
            }
        }
		
		triggers { 
		   pollSCM('H/2 * * * *') 
		}
        
		stages {
			   stage ("deploy index") {
			          steps {
					  sh ''' 
					  cp index.html /var/www/html/
					  chmod 777 /var/www/html/index.html
					  systemctl restart httpd
					  '''
					  }
			   }
			   
		
		}
}
