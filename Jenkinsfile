node {
    def userInput = false
    stage('Preparation') { // for display purposes
        userInput = input(id: 'Proceed1', message: 'Promote build?', parameters: [[$class: 'BooleanParameterDefinition', defaultValue: true, description: '', name: 'Please confirm you agree with this']])
        echo 'userInput: ' + userInput

        if(userInput == true) {
            echo "Action was approved"
            sh '/home/ubuntu/bin/kubectl get nodes'

            } else {
                // not do action
                echo "Action was aborted."
            }

         
        
    }
    stage('Build') {
    sh 'echo "Hello World"'
        
    }
    
}
