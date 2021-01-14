node {
    def userInput = false
    withAWS(credentials: 'aws-key', region: 'us-east-2') {
    sh 'aws iam get-user'
}
    stage('Preparation') { // for display purposes
        withCredentials([[$class: 'com.cloudbees.plugins.credentials.common.StandardUsernamePasswordCredentials', credentialsId: 'aws-key', usernameVariable: 'AWS_ACCESS_KEY_ID', passwordVariable: 'AWS_SECRET_ACCESS_KEY']]) {
        
    
        userInput = input(id: 'Proceed1', message: 'Promote build?', parameters: [[$class: 'BooleanParameterDefinition', defaultValue: true, description: '', name: 'Please confirm you agree with this']])
        echo 'userInput: ' + userInput

        if(userInput == true) {
            echo "Action was approved"
            sh 'aws eks --region us-east-2 update-kubeconfig --name fargate-poc'
            sh '/home/ubuntu/bin/kubectl get nodes'

            } else {
                // not do action
                echo "Action was aborted."
            }
        }

         
        
    }
    stage('Build') {
    sh 'echo "Hello World"'
        
    }
    
}
