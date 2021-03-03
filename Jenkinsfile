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
                    cucumber failedFeaturesNumber: -1, failedScenariosNumber: -1, failedStepsNumber: -1, fileIncludePattern: '**/*.json', pendingStepsNumber: -1, skippedStepsNumber: -1, sortingMethod: 'ALPHABETICAL', undefinedStepsNumber: -1
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
