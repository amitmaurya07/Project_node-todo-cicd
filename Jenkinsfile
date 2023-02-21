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
                sh 'docker build -t amaurya07/to-do-django-react:1 .'
                echo "Build the code on the Docker Agent"
            }
        }

        stage("Pushing the Image to DockerHub")
        {
            steps{
                withCredentials([string(credentialsId: 'amaurya07', variable: 'dockerhubpasswd')]) 
                {
                    sh 'docker login -u amaurya07 -p $(dockerhubpasswd)'
                    sh 'docker push amaurya07/to-do-django-react:1'
 
                 }
                
            }        

        }
        
        stage("Run the Container")
        {    
            steps{
                sh 'docker run -d --name django-container -p 8000:8000 to-do-django-react:1'
            }
        }
    }
}