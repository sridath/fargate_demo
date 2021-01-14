node {
    def userInput = false
    stage('git clone'){
        checkout scm
    }
    stage('Preparation') { // for display purposes
        withAWS(credentials: 'aws-key', region: 'us-east-2') {
        
        sh 'aws eks --region us-east-2 update-kubeconfig --name eks-fargate-ex'
        sh '/home/ubuntu/bin/kubectl get nodes'
        userInput = input(id: 'Proceed1', message: 'Deploy in fargate?', parameters: [[$class: 'BooleanParameterDefinition', defaultValue: true, description: '', name: 'Please confirm you agree with this']])
        echo 'userInput: ' + userInput

        if(userInput == true) {
            echo "deploying with fargate profile"
            sh '/home/ubuntu/bin/kubectl apply -f fargate.yaml'
            
            
            
            } else {
                // not do action
                echo "deploying in eks worker node"

                sh '/home/ubuntu/bin/kubectl apply -f namespace.yaml -f deployment.yaml -f service.yaml -f ingress.yaml'
            }

        }

         
        
    }
    stage('Build') {
    sh 'echo "Hello World"'
        
    }
    
}
