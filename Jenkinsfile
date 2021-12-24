
node {    
                      
            checkout scm      
     
            docker.withRegistry('https://registry.hub.docker.com', 'docker') {   
                  def customImage = docker.build("lovetha/test-image")
             
              /*  */
               customImage.push()
           }
        }
