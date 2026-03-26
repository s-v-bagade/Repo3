pipeline {
agent any

environment {
    CONTAINER_NAME = "my-httpd-container"
    IMAGE_NAME = "httpd:latest"
}

stages {

    stage('Pull Image') {
        steps {
                docker.image("${IMAGE_NAME}").pull()
            }
    }

    stage('Run Container') {
        steps {
                sh """
                docker rm -f ${CONTAINER_NAME} || true
                docker run -dit --name ${CONTAINER_NAME} -p 8080:80 ${IMAGE_NAME}
                """
        }
    }

    stage('Copy index.html to Container') {
        steps {
            
                sh """
                docker cp index.html ${CONTAINER_NAME}:/usr/local/apache2/htdocs/index.html
                """
            
        }
    }

}


}
