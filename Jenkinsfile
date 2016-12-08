node {
  stage 'Checkout'
    /* Checkout the code we are currently running against */
    checkout scm

  stage 'Build'
    /* Build the Docker image with a Dockerfile, tagging it with the build number */
    def app = docker.build "artirix/our-app:${env.BUILD_NUMBER}"

  stage 'Test'
    /* We can run tests inside our new image */
    app.inside {
      sh '/app/run_tests.sh'
    }    

  stage 'Publish'
    /* Push the image to Docker Hub, using credentials we have setup separately on the worker node */
    app.push 'latest'
}
