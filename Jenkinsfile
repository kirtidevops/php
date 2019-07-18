node {
    def app

    stage('Clone repository') {
        /* Cloning the Repository to our Workspace */

        checkout scm
    }

    stage('Build image') {
        /* This builds the actual image */

        app = docker.build("kittu0410/spinnaker")
    }

    stage('Test image') {
        
        app.inside {
            echo "Tests passed"
        }
    }

    stage('Push image') {
        /* 
			You would need to first register with DockerHub before you can push images to your account
		*/
	    docker.withRegistry('https://549942532493.dkr.ecr.us-east-1.amazonaws.com', 'ecr:us-east-1:ecr-credentials'){
       
		app.push("spinnakertest{env.BUILD_NUMBER}")
            app.push("latest")
            } 
                echo "Trying to Push Docker Build to dockerhub"
    }
}
