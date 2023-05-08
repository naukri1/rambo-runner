pipeline {

  agent any 
  stages {

      stage("Pull latest Image") {

         steps {

             bat "docker pull neopane1/finalone"
         }

      }


        stage("Start grid") {

         steps {

             bat "docker-compose up -d hub chrome firefox"
         }

      }

        stage("Run test") {

         steps {

             bat "docker-compose up search book"
         }

      }
  }
    post{
        always {

            archiveArtifacts artifacts:'output/**'
            bat "docker-compose down"
        }

    }
}
