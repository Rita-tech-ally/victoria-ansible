@Library('ansible-lib') _

pipeline {
    agent any

    stages {

        stage('Load Config') {
            steps {
                script {
                    def config = readYaml file: 'config.yaml'

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
