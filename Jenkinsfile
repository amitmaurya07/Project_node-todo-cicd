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
            agent{
                docker{
                    image 'amaurya07/to-do-django-react:1'
                    reuseNode true
                    
                }
            }
                 steps{
                    echo 'Image has been built'
                 }
        }

        stage("Pushing the Image to DockerHub")
        {
            steps{
                withCredentials([string(credentialsId: 'amaurya07', variable: 'dockerhubpasswd')]) 
                {
                    sh 'docker login -u amaurya07 -p ${dockerhubpasswd}'
                    sh 'docker push amaurya07/to-do-django-react:1'
 
                 }
                
            }        

        }
        
        stage("Run the Container")
        {    
            steps{
                sh 'docker run -d --name django-container -p 8000:8000 amaurya07/to-do-django-react:1'
            }
        }
    }
}