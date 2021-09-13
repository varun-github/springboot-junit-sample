@Library('jenkins-library') import com.varun.jenkins.Utils
def utils = new Utils(this)

pipeline {
    agent any
    stages {
        stage('Build') {
            steps {
                script {
                    utils.withMaven do: "package", withArgFile: ".jenkins/stage.build.env.json"
                }
            }
        }
    } 
    post {
        always {
            script{
                utils.withCloudStudio do: "emitTelemetry"
            }
        }
}

}