pipeline {
	agent any

stages {
	stage ('Parallel'){
		parallel {
			stage	('Stage-1')
			{
				steps{
				echo "Welcome to Project1 !"
				sleep 5
				}
			}	
			stage	('Stage-2')
			{
				steps{
				echo "Project Started !"
				sleep 5
				}
			}
			stage	('Stage-3')
			{
				steps{
				echo "Project Ended!"
				sleep 5
				}
			}	
	

		}
	}
  }
}
