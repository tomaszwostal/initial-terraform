pipeline
{
    options
    {
        buildDiscarder(logRotator(numToKeepStr: '5'))
        timestamps()
        timeout(time: 30, unit: 'MINUTES')
    }
    agent any
    stages
    {
        stage('Say Hello')
        {
            steps
            {
                script
                {
                    sh ('echo \"Hello\"')
                }
            }
        }
        stage('Say Goodbye')
        {
            steps
            {
                script
                {
                    sh ('echo \"Goodbye\"')
                }
            }
        }

    post
    {
        always
        {
            // make sure that the Docker image is removed
            sh "docker rmi $IMAGE | true"
	    //emailext body: '''$PROJECT_NAME - Build # $BUILD_NUMBER - $BUILD_STATUS:

		//Check console output at $BUILD_URL to view the results.''', recipientProviders: [[$class: 'RequesterRecipientProvider'], [$class: 'UpstreamComitterRecipientProvider']], replyTo: 'cloud@slabs.pl', subject: '$PROJECT_NAME - Build # $BUILD_NUMBER - $BUILD_STATUS!', to: '$DEFAULT_RECIPIENTS '

        }
    }
}
}