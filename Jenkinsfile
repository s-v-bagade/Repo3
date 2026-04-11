pipeline {
        agent {
            label {
            label 'built-in'
            customWorkspace "/mnt/project"
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
