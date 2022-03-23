pipeline {
    agent any

    stages {
        stage('Build') {
            when {
                equals(actual: currentBuild.number, expected: 1)
            }
            steps {
                echo 'Building the application..will run only during FIRST build'
            
            }
        }
        stage('Test') {
            when {
               expression {
                    env.BRANCH_NAME == 'main' || env.BRANCH_NAME == 'master'
               }
            }
            steps {
                echo 'Testing the application..will run only when branch is main or master'
            }
        }
        stage('Deploy') {
            when {
                expression {
                    return env.BRANCH_NAME != 'master';
                }
            }
            steps {
                echo 'Deploying the application....will run only if branch is NOT EQUAL to master'
            }
        }
        stage('Launch') {
            when { 
               environment name: 'NAME', value: 'batman' 
            }
           steps {
                echo 'Launch the application....will run only if environment variable name has value of batman'
           }
        }
    }
    
    post{
        always{
            echo "========always========"
        }
        success{
            echo "========pipeline executed successfully ========"
        }
        failure{
            echo "========pipeline execution failed========"
        }
    }
}
