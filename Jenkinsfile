pipeline {
    agent any

    stages {
        stage ('Compile Stage') {

            steps {
                withMaven(maven : 'Maven 3.6') {
                    sh 'mvn clean compile'
                }
            }
        }

        stage ('Testing Stage') {

            steps {
                withMaven(maven : 'Maven 3.6') {
                    sh 'mvn test'
                }
            }
            post{
                always{
                    cucumber fileIncludePattern: '**/*.json', sortingMethod: 'ALPHABETICAL'
                }
            }
                
        }

        stage ('Deployment Stage') {
            steps {
                withMaven(maven : 'Maven 3.6') {
                    sh 'mvn deploy'
                }
            }
        }
    }
}
