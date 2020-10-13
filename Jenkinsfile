pipeline {
    agent any
    parameters {
        string(name: 'DOCKER_IMAGE_VERSION', defaultValue: 'latest', description: 'Image Name')
    }
    stages {
        stage('Updating image version') {
            steps {
                sh "sed -i '' 's/imageVersion/${params.DOCKER_IMAGE_VERSION}/' prod-consumer-ui-deployment.yml"
            }
        }
        stage('Deploy to Kubernetes') {
            steps {
                sh "kubectl apply -f ."
            }
        }
    }
}