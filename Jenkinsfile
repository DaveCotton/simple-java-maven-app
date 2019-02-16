pipeline {
    agent any

    stages {
        /* stage('Build') {
          steps {
              sh 'mvn -B -DskipTests clean package'
          }
        } */
        stage('DeployToStaging') {
            steps {
                sshPublisher(
                    failOnError: true,
                    continueOnError: false,
                    publishers: [
                        sshPublisherDesc(
                            configName: 'SSH-JavaServer-1', 
                            transfers: [
                                sshTransfer(
                                    sourceFiles: 'target/my-app.jar',
                                    removePrefix: 'target/',
                                    remoteDirectory: '.')
                            ]
                        )
                    ]
                )
            }
        }
    }
}
