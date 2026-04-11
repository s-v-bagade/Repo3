pipeline {
        agent {
            label 'node2'  
        }
		
		triggers { 
		   pollSCM('H/2 * * * *') 
		}
        
		stages {
			   stage ("deploy index") {
			          steps {
					  sh ''' 
					  sudo cp index.html /var/www/html/
					  sudo chmod 777 /var/www/html/index.html
					  sudo systemctl restart httpd
					  '''
					  }
			   }
			   
		
		}
}
