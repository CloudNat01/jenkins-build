node {
    checkout scm

    docker.withRegistry('https://registry.hub.docker.com', 'cloudnat-dockerhub') {

        def customImage = docker.build("sample:${env.BUILD_ID}")

        /* Push the container to the custom Registry */
        customImage.push()
    }
}
