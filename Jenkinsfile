pipeline {

        agent {
            label {
            label 'built-in'
            customWorkspace "/mnt/project"
            }
        }

        stages {

               stage('Pull Image') {
                    steps {
			        script {
                          docker.image("httpd:latest").pull()
                        }
					}
                }

                stage('Run Container') {
                    steps {
                     sh """
                     docker rm -f c1
                     docker run -itd --name c1 -p 80:80 httpd:latest
                     """
                    }
                }

                stage('Copy index.html to Container') {
                    steps {
                    sh """
                    docker cp index.html c1:/usr/local/apache2/htdocs/index.html
					docker exec c1 chmod 777 /usr/local/apache2/htdocs/index.html
                    """
					} 
                }

        }


    }  
