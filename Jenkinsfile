pipeline{
    
    agent { label "dev"};
    
    stages{
        stage("Code Clone"){
            steps{
               script{
                   clone("git@github.com:sahastra16/two-tier-flask-app-new.git", "prd")
               }
            }
        }
        stage("Trivy File System Scan"){
            steps{
                script{
                    trivy_fs()
                }
            }
        }
        stage("Build"){
            steps{
                sh "docker build -t two-tier-flask-app ."
            }
            
        }
        stage("Test"){
            steps{
                echo "Developer / Tester tests likh ke dega..."
            }
            
        }
        stage("Deploy"){
            steps{
                sh "docker compose up -d --build flask-app"
            }
        }
    }

post{
        success{
            script{
                emailext from: 'kedar.sahasrabudhe@gmail.com',
                to: 'kedar.sahasrabudhe@hotmail.com',
                body: 'Build success for Demo CICD App',
                subject: 'Build success for Demo CICD App'
            }
        }
        failure{
            script{
                emailext from: 'kedar.sahasrabudhe@gmail.com',
                to: 'kedar.sahasrabudhe@hotmail.com',
                body: 'Build Failed for Demo CICD App',
                subject: 'Build Failed for Demo CICD App'
            }
        }
    }
}
