pipeline
{
    agent any
    stages
    {
        stage("Clean")
        {
            steps
            {
                sh ' sudo rm -rf /var/lib/jenkins/workspace/Docker/* '
                sh ' docker stop $(docker ps -a -q) '
                sh ' docker rm $(docker ps -a -q) '
                sh ' docker rmi $(docker images -q) '
            }
        }
        stage("Clone")
        {   
            steps
            {
                sh ' sudo git clone -b python https://github.com/Shashankp21/totask.git '
            }
        }
        stage("Build")
        {
            steps
            {
                sh ' sudo docker build -t app /var/lib/jenkins/workspace/Docker/Docker-jenkins-tasks  '
            }
        }
        stage("Run")
        {
            steps
            {
                sh ' sudo docker run -it -d app '
            }
        }
    }
    post 
    {
        success 
        {
            echo 'Build successful!'
        }
        failure 
        {
            echo 'Build failed!'
        }
    }
}