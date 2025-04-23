pipeline {
    agent any
    
    parameters {
        choice(
            name: 'ENVIRONMENT',
            choices: ['STG', 'PRD'],
            description: 'Select the target environment'
        )
        choice(
            name: 'ACTION',
            choices: ['START', 'STOP'],
            description: 'Select the action to perform'
        )
    }

    
stages{



stage('checkout')

    {
      steps{
          git credentialsId: '95801cb0-a4a2-4452-9442-267525aeca71', url: 'https://github.com/Jean2425/work.git'
        }
    }
  }

  stage('Validate Input') {
            steps {
                script {
                    echo "Selected Environment: ${params.ENVIRONMENT}"
                    echo "Selected Action: ${params.ACTION}"
                }
            }
        }
}
