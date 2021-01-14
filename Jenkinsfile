node {
    def userInput = false
    stage('Preparation') { // for display purposes
        withAWS(credentials: 'aws-key', region: 'us-east-2') {
        
    
        userInput = input(id: 'Proceed1', message: 'Promote build?', parameters: [[$class: 'BooleanParameterDefinition', defaultValue: true, description: '', name: 'Please confirm you agree with this']])
        echo 'userInput: ' + userInput

        if(userInput == true) {
            echo "Action was approved"
            sh 'aws eks --region us-east-2 update-kubeconfig --name fargate-poc'
            sh '/home/ubuntu/bin/kubectl get nodes'
            sh '/home/ubuntu/bin/kubectl apply -f namespace.yaml -f deployment.yaml -f service.yaml -f ingress.yaml'
            
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
