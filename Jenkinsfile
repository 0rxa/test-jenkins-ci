pipeline {
	environment {
		IMAGE = "registry.lca.com/test-backend"
		REGISTRY_CREDENTIALS = "lca-local-registry-credentials"
	}

	stages {
		stage("Build docker image") {
			steps {
				script {
					docker.build IMAGE
				}
			}
		}
	}
}
