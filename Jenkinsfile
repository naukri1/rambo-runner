pipeline {

  agent any 
  stages {

      stage("Pull latest Image") {

         steps {

             sh "docker pull neopane1/finalone"
         }

      }


        stage("Start grid") {

         steps {

             sh "docker-compose up -d hub chrome firefox"
         }

      }

        stage("Run test") {

         steps {

             sh "docker-compose up search book"
         }

      }
  }
    post{
        always {

            archiveArtifacts artifacts:'output/**'
            sh "docker-compose down"
        }

    }
}