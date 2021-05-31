pipeline {
  agent any
	environment {
		IMAGE = "registry.lca.com/test-backend"
    REGISTRY = "https://registry.lca.com"
		REGISTRY_CREDENTIALS = "lca-local-registry-credentials"
	}

	stages {
		stage("Build and push docker image") {
			steps {
				script {
					REMOTE_IMAGE = docker.build IMAGE
          docker.withRegistry(REGISTRY, REGISTRY_CREDENTIALS) {
            REMOTE_IMAGE.push()
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
