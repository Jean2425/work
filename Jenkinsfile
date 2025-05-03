//mine
pipeline {

    agent any
    //{  label 'Jenkinsansiblenode'}
    
    options {
  buildDiscarder logRotator(artifactDaysToKeepStr: '', artifactNumToKeepStr: '', daysToKeepStr: '7', numToKeepStr: '10')
}
    
environment{
    AWS_EC2_PRIVATE_KEY=credentials('ec2-private-key')
}
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

stage('Validate Input') {
            steps {
                script {
                    echo "Selected Environment: ${params.ENVIRONMENT}"
                    echo "Selected Action: ${params.ACTION}"
                }
            }
        }
        
stage('checkout')

    {
      steps{
          git credentialsId: '95801cb0-a4a2-4452-9442-267525aeca71', url: 'https://github.com/Jean2425/work.git'
        }
    }

stage('Ping')

    {
      steps{
          sh "whoami"
          sh "hostname"
          sh "ansible-playbook -i inventory/hosts --private-key=$AWS_EC2_PRIVATE_KEY playbooks/01ping.yaml --ssh-common-args='-o StrictHostKeyChecking=no'"
        }
    }

/*
stage('checkout')

    steps{
          sscript {
                    if (params.ENVIRONMENT == 'STG') {
                        // PRD Environment Operations
                        stage('tomcat_stg_1') {
                            ansiblePlaybook(
                                playbook: "${params.ACTION}_tomcat.yml",
                                inventory: 'inventory_prd',
                                extraVars: [
                                    server: 'tomcat_stg_1'
                                ]
                            )
                            
                        }
                    }
          }
    }
    */
  } // stages closing
} // pipeline closing
