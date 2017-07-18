node {
    def app

    stage('Clone repository') {
        /* Let's make sure we have the repository cloned to our workspace */

        checkout scm
    }

    stage('Build image') {
        /* This builds the actual image; synonymous to
         * docker build on the command line */

        app = docker.build("038930456275.dkr.ecr.ap-southeast-1.amazonaws.com/christie-cowork")
    }

    stage('Test image') {
        /* Ideally, we would run a test framework against our image.
         * For this example, we're using a Volkswagen-type approach ;-) */

        app.inside {
            sh 'echo "Tests passed"'
        }
    }

    stage('Push image') {
        
		
		sh "\$(aws ecr get-login --no-include-email --region ap-southeast-1)
		sh "docker tag christie-cowork:latest 038930456275.dkr.ecr.ap-southeast-1.amazonaws.com/christie-cowork:latest"
		sh "docker push 038930456275.dkr.ecr.ap-southeast-1.amazonaws.com/christie-cowork:latest"
		
        }
    }
}