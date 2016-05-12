#!groovy

node {
    try {
        stage 'Build'
        //git url: 'https://github.com/jfouqueray/helloworld.git'
        checkout scm
        def mvnHome = tool 'Maven 3.3.9'
        sh "${mvnHome}/bin/mvn -B -f pom.xml install"
        slackSend: 'END'

        stage 'Deploy DEV'
        echo 'Deployment in DEV'

        stage 'Test DEV'
        echo 'Testing in DEV'

        stage 'Deploy UAT'
        echo 'Deployment in UAT'

        stage 'Test UAT'
        echo 'Testing in UAT'
        slackSend message: "SUCCESS: ${env.JOB_NAME} #${env.BUILD_NUMBER}", color: "#00CC00"
    }
    catch (caughtError) {
        slackSend message: "FAILURE: ${env.JOB_NAME} #${env.BUILD_NUMBER}", color: "#CC0000"
        throw caughtError
    }
}