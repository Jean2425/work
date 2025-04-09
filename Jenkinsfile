pipeline 
{
agent any 

parameters {
  choice choices: ['STG', 'PROD'], name: 'Choose Env'
}


stages{
stage('checkout')
    {
      steps{
          git credentialsId: '95801cb0-a4a2-4452-9442-267525aeca71', url: 'https://github.com/Jean2425/work.git'
        }
    }
  }
}
