
node {    
                      
            checkout scm      
     
            docker.withRegistry('https://registry.hub.docker.com', 'docker-hub') {   
                  def customImage = docker.build("test-image")
             
              /*  */
                  customImage.push()
           }
        }
