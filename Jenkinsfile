pipeline{
	agent {
		label{
		label 'slave1'
		}
	}
	stages{
		stage('git clone'){
			steps{
				checkout([$class: 'GitSCM', branches: [[name: '*/main']], extensions: [], userRemoteConfigs: [[credentialsId: 'github-id', url: 'https://github.com/Abisola-etech/abi-parallel.git']]])
			}
		}
	stage('parallel-level'){
		parallel{
			stage('sub-job1 abisola'){
				steps{
					echo "sub-job1 task"
				}
			}
			stage('sub-job2'){
				steps{
					echo "sub-job2 task"
				}
			}
			stage('webhook'){
				steps{
					 echo "just trying the 3rd line"
				}
			}
		}
	}
	stage('version-check'){
		agent{
			label{
			label 'slave2'
			}
		}
		steps{
			echo "end of parallel job"
		}
	}
	stage('usercheck'){
		steps{
			sh 'cat /etc/passwd'
		}
	}
	}
}
