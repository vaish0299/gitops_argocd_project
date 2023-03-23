pipeline
{
    agent any

    environment
    {

        DOCKERHUB_USERNAME = "vaish0299"
        APP_NAME = "gitops-argo-app"
        IMAGE_TAG = "${BUILD_NUMBER}"
        IMAGE_NAME = "${DOCKERHUB_USERNAME}"+"/"+"${APP_NAME}"
        REGISTRY_CREDS = "dockerhub"
    }
    
    stages
    {
        stage('clean workspace')
        {
        steps
        {
            script
            {
                cleanWs()
            }
        }
        }
        stage('Checkout SCM')
        {
            steps
            {
                script
                {
                    git credentialsId: 'github',
                    url: 'https://github.com/vaish0299/gitops_argocd_project.git',
                    branch : 'main'
                }
                // withCredentials([gitUsernamePassword(credentialsId: 'github', gitToolName: 'Default')])
                //  {
                //          // some block
                //          // url: 'git@github.com:vaish0299/gitops_argocd_project2.git'
                //  }
            }
        }
        stage('Build Docker image')
        {
            steps
            {
                script
                {
                    docker_image = docker.build "${IMAGE_NAME}"
                }
            }
        }
        stage('Push Docker Image')
        {
            steps
            {
                script
                {
                   docker.withRegistry('',REGISTRY_CREDS)
                   {
                    docker_image.push("${BUILD_NUMBER}")
                    docker_image.push('latest')
                   } 
                }
            }
        }
        stage('Delete Docker images')
        {
            steps
            {
                sh "docker rmi ${IMAGE_NAME}:${IMAGE_TAG}"
                sh "docker rmi ${IMAGE_NAME}:latest"
            }
        }
        stage('Updating kubernetes Deployment file')
        {
            steps
            {
              sh """
              cat deployment.yml
              sed -i 's/${APP_NAME}.*/${APP_NAME}:${IMAGE_TAG}/g' deployment.yml
              cat deployment.yml
              """
            }
        }
    }
}