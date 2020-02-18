pipeline {
    agent any
    options {
        //ansiColor('xterm')
        buildDiscarder(logRotator(numToKeepStr:'10'))
        disableConcurrentBuilds()
        timeout(time: 5, unit: 'MINUTES')
        timestamps()
    }
    environment {
      GIT_GROUP = 'sundarprince86'
      APPLICATION_NAME = 'apigee-config-maven-plugin'
      SOURCE_REPO_URI = "${GIT_GROUP}" + '/' + "${APPLICATION_NAME}"
      SOURCE_BRANCH = "master"
    }
    stages {
        stage('Checkout') {
            steps {
                script {
                    ansiColor('xterm') {
                        checkoutRepository(repository: SOURCE_REPO_URI, branch: SOURCE_BRANCH)
                    }
                }
            }
        }

        stage ('Create caches') {
            steps {
                script {
                    ansiColor('xterm') {
                        sh "mvn clean install"
                        sh "mvn apigee-config:caches -Ptest -Dapigee.config.options=update -Dapigee.config.dir=apigee-config/samples/EdgeConfig/resources/edge/"
                        echo "Inside deploy stage"
                    }
                }
            }
        }

	stage ('Unit Test and Build') {
            steps {
                script {
                    ansiColor('xterm') {
                        //sh "mvn clean install"
                        echo "Inside Unit Test and Build Stage"
                    }
                }
            }
        }
	}
}
