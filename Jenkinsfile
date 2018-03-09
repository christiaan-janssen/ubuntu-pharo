node("docker-agent") {
    def app

    stage('Clone repository') {
        /* Let's make sure we have the repository cloned to our workspace */

        checkout scm
    }

    stage('Build image') {
        /* This builds the actual image; synonymous to
         * docker build on the command line */
        app = docker.build("shidima/ubuntu-pharo:${env.BUILD_ID}")
    }
    
    staget('Push Image') {
        docker.withRegistry('https://registry.example.com', 'dockerhub') {
            app.push()  
            app.push('latest')
        }
    }
}
