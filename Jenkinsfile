pipeline {
    agent any

    stages {
        stage('Deploy') {
            steps{
                withCredentials([azureServicePrincipal('azurefem')]) {
                    // sh 'echo $AZURE_SUBSCRIPTION_ID'
                    // sh 'echo $AZURE_CLIENT_ID'

                    //echo "${env.AZURE_CLIENT_ID}"
                    sh "az login --service-principal -u $AZURE_CLIENT_ID --password $AZURE_CLIENT_SECRET  --tenant $AZURE_TENANT_ID --verbose"
                    sh 'az account list --output table --verbose'
                    sh 'echo $RESORUCE_GROUP_NAME'
                    
                    sh "az group create \
                    --name $RESOURCE_GROUP_NAME \
                    --location $LOCATION"

                    echo 'End of Deployment'
                }
            }
        }
    }
}