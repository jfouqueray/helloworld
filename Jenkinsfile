#!groovy

node {
    try {
        stage 'Build'
        //git url: 'https://github.com/jfouqueray/helloworld.git'
        checkout scm
        def mvnHome = tool 'Maven 3.3.9'
        sh "${mvnHome}/bin/mvn -B -f pom.xml install"
        //slackSend: 'END'

        stage 'Build Docker image'
        //sh "docker build -t jfouqueray/helloworld"
        image = docker.build("jfouqueray/helloworld")
        echo 'Build Docker image'

        stage 'Run docker image'
        echo 'Run docker image'

        stage 'Push image into registry'
        echo 'Push image into registry'

        //slackSend message: "SUCCESS: ${env.JOB_NAME} #${env.BUILD_NUMBER}", color: "#00CC00"
    }
    catch (caughtError) {
        //slackSend message: "FAILURE: ${env.JOB_NAME} #${env.BUILD_NUMBER}", color: "#CC0000"
        throw caughtError
    }
}
