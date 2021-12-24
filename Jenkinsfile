
node {    
                      
            checkout scm      
     
            docker.withRegistry('https://registry.hub.docker.com', 'docker-hub') {   
                  def customImage = docker.build("lovetha/test-image")
             
              /*  */
                  customImage.push()
           }
        }
