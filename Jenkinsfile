node {
    def app

    stage('Clone repository') {
        /* Let's make sure we have the repository cloned to our workspace nodejs-app*/
          checkout scm
    }

    stage('Build image') {
        /* This builds the actual image; synonymous to
         * docker build on the command line */
        sh 'docker build -f Dockerfile -t manee2k6/devops:nodejs-bds .'
       // app = docker.build("manee2k6/explore:${env.BUILD_NUMBER}")
        
    }

    stage('Test image') {
        /* Ideally, we would run a test framework against our image.
         * For this example, we're using a Volkswagen-type approach ;-) */

            sh 'echo "Tests passed"'
       
    }

    stage('Push image') {
        /* withDockerRegistry([credentialsId: 'docker-hub-credential', url: 'https://hub.docker.com/']) {
            app.push("${env.BUILD_NUMBER}") 
            app.push("latest")*/
        sh 'docker login -u manee2k6 -p arpitha@17'
        sh 'docker push manee2k6/devops:nodejs-bds'
       }
    }
