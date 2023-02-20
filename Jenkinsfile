pipeline{
    agent any 
    stages{
        stage("Code")
        {
            steps{
                git 'https://github.com/amitmaurya07/Project_node-todo-cicd.git'
            }
        }
        stage("Build the Docker Image")
        {
            steps{
                sh 'docker build -t django-react:1 .'
            }
        }
        stage("Run the Container")
        {    
            steps{
                sh 'docker run -d --name django-container -p 8000:8000 django-react:1'
            }
        }
    }
}