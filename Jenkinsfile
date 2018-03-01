#!groovy

def kubectlTest() {
    // Test that kubectl can correctly communication with the Kubernetes API
    echo "running kubectl test"
    sh "kubectl get nodes"
}

def helmInstall() {
    // Test that helm can correctly communication with the Kubernetes API
    echo "running helm test"
  	sh 'helm init'
  	sh 'helm install --name myemp myemp/'
}

def helmUpgrade() {
    // Test that helm can correctly communication with the Kubernetes API
  	sh 'helm upgrade myemp myemp/'
    sh 'helm history myemp'
}

node {
    def app

    stage('Clone repository') {
        // Let's make sure we have the repository cloned to our workspace

        checkout scm
    }

    stage('Build image') {
        /* This builds the actual image; synonymous to
         * docker build on the command line */

        /*app = docker.build("ernesen/uae-icp-demo")*/
	       app = docker.build("${env.IMAGE_BUILD}")
    }

    stage('Test image') {
        // Ideally, we would run a test framework against our image.

        app.inside {
            sh 'echo "Tests passed"'
        }
    }

    stage('Push image') {
        /* Finally, we'll push the image with two tags:
         * First, the incremental build number from Jenkins
         * Second, the 'latest' tag.
         * Pushing multiple tags is cheap, as all the layers are reused. */
        docker.withRegistry('https://registry.hub.docker.com', 'docker-hub-credentials') {
            app.push("${env.BUILD_NUMBER}")
            app.push("latest")
        }
    }

    stage('Deploy Helm') {
        // Let's make sure we can run helm on this server
        //helmTest()
        //helmUpgrade()
        //sh 'echo "Tests passed"'
        //sh  'helm upgrade myemp myemp/'
        //sh  'helm list'
        //sh  'helm rollback myemp 1'
        //sh  'helm ls --all myemp'
    }
}
