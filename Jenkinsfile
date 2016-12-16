node("docker") {
    docker.withRegistry("https://registry.hub.docker.com") {
    
        git url: "https://github.com/jamespowell99/docker-example.git"
    
        sh "git rev-parse HEAD > .git/commit-id"
        def commit_id = readFile('.git/commit-id').trim()
        println commit_id
    
        stage "build"
        def app = docker.build "your-project-name"
    
        stage "publish"
        app.push 'master'
        app.push "${commit_id}"
    }
}
