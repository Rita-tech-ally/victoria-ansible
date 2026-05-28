@Library('ansible-lib') _

pipeline {
    agent any

    stages {

        stage('Load Config') {
            steps {
                script {

                    def config = readYaml file: 'config.yaml'

                    withAWS(credentials: 'aws-creds', region: 'ap-south-1') {

                        withEnv([
                            "AWS_REGION=ap-south-1",
                            "AWS_DEFAULT_REGION=ap-south-1"
                        ]) {

                            ansibleDeploy(
                                SLACK_CHANNEL_NAME : config.SLACK_CHANNEL_NAME,
                                ENVIRONMENT        : config.ENVIRONMENT,
                                CODE_BASE_PATH     : '.',
                                ACTION_MESSAGE     : config.ACTION_MESSAGE,
                                KEEP_APPROVAL_STAGE: config.KEEP_APPROVAL_STAGE,
                                REPO_URL           : 'https://github.com/Rita-tech-ally/victoria-ansible.git'
                            )
                        }
                    }
                }
            }
        }
    }
}
