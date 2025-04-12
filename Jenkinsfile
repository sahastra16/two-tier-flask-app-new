pipeline{
    
    agent { label "dev"}
    
    stages{
        stage("Code Clone"){
            steps{
               script{
                    git url: 'https://github.com/sahastra16/two-tier-flask-app-new.git', branch: 'prd'
               }
            }
        }

    stage("Build"){
            steps{
                sh "docker build -t two-tier-flask-new ."
            }
            
        }
        stage("Test"){
            steps{
                echo "Developer / Tester tests likh ke dega..."
            }
            
        }
        stage("Deploy"){
            steps{
                sh "docker compose down && docker compose up -d"
            }
        }    
    }

}
