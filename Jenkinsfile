pipeline {
    agent any
	
    stages {
        stage('Git-Checkout') {
            steps {
                    echo "Checking out from Git Repo";
                    git credentialsId: 'e9618335-9197-4120-a0fb-ed96bcba9507', url: 'https://github.com/SachinChs/shell-script.git'
            }
        }
        
        stage('Build') {
            steps {
                    echo "Building the checked-out project!";
                     sh './build.sh'
            }
        }
        
        stage('Unit-Test') {
            steps {
                    echo "Running JUnit Tests"; 
                    sh './unit.sh'
             }
        }
        
        stage('Quality-Gate') {
            steps {
                  echo "Verifying Quality Gates";
                  sh './quality.sh'

            }
        }
        
		stage('Deploy') {
            steps {
                  echo "Deploying to Stage Environment for more tests!";
                  sh './deploy.sh'
            }
        }
    }
    post {
        always {
            echo 'This will always run'
        }
        success {
            echo 'This will run only if successful'
        }
        failure {
            echo 'This will run only if failed'
        }
        unstable {
            echo 'This will run only if the run was marked as unstable'
        }
        changed {
            echo 'This will run only if the state of the Pipeline has changed'
            echo 'For example, if the Pipeline was previously failing but is now successful'
        }
    }
}
