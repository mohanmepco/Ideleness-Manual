pipeline {
    agent {
        node {
            label 'master'
        }
    }

    stages {

        stage('Instance Idleness check') {
            steps {
                sh 'echo "Started...!" '
            }
        }
        stage('git clone') {
            steps {
                sh 'rm -r *; git clone https://github.com/mohanmepco/Ideleness-Manual.git'
            }
        }
		stage('PersmissionToExecute'){
            steps {
                sh 'cd //root/.jenkins/workspace/Idleness-Manual/Ideleness-Manual; chmod 755 Idleness-script'
            }
        }
		stage('InstanceDetails'){
            steps {
                sh 'cd /root/.jenkins/workspace/Idleness-Manual/Ideleness-Manual; aws ec2 describe-instances --instance-id i-0fd0d170e806cd7cc >instance.txt'
			}
		}
		stage('CheckIdleness'){
            steps {
                sh 'cd /root/.jenkins/workspace/Idleness-Manual/Ideleness-Manual; sh Idleness-script'
			}
		}
	}
}
