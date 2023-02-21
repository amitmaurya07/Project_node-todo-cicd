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
                docker {
                    image 'amaurya07/to-do-django-react:1'
                    reuseNode true
                }
            }
            steps{
                echo "Build the code on the Docker Agent"
            }
        }

        stage("Pushing the Image to DockerHub")
        {
            steps{
                withCredentials([usernamePassword(credentialsId: 'DockerHub', passwordVariable: 'DockerHub Password', usernameVariable: 'DockerHub')]) {
                    sh 'docker push amaurya07/to-do-django-react:1 '
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