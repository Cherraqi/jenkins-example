pipeline {
    agent any
    def mvnHome
    mvnHome=tool 'M3'
    stages {
        stage ('Compile Stage') {

            steps {

                    sh "'${mvnHome}/bin/mvn' clean compile"
            }
            
        }

        stage ('Testing Stage') {

            steps {

                    sh "'${mvnHome}/bin/mvn' test"
            
            }
        }


        stage ('Deployment Stage') {
            steps {

                    sh "'${mvnHome}/bin/mvn' deploy"
                
            }
        }
    }
}
