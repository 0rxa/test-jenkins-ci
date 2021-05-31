pipeline {
  agent any
	environment {
		IMAGE = "registry.lca.com/test-backend"
		REGISTRY_CREDENTIALS = "lca-local-registry-credentials"
	}

	stages {
		stage("Build and push docker image") {
			steps {
				script {
					docker.build IMAGE
          docker.withRegistry('', REGISTRY_CREDENTIALS) {
            IMAGE.push()
          }
				}
			}
		}
    stage("Apply kubernetes manifests") {
      steps {
        sh '''
          kubectl apply -k kubernetes/
          '''
      }
    }
	}
}
