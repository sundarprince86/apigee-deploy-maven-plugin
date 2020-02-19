pipeline {
    agent any
    environment {
      GIT_GROUP = 'sundarprince86'
      APPLICATION_NAME = 'apigee-config-maven-plugin'
      SOURCE_REPO_URI = "${GIT_GROUP}" + '/' + "${APPLICATION_NAME}"
      SOURCE_BRANCH = "master"
    }
    stages {
        stage ('Create caches') {
            steps {
                script {
                        sh "mvn clean install"
                        sh "mvn install -Ptest -Dusername=sundarprince86@gmail.com -Dpassword=Johanna@2020 -Dapigee.config.options=update"
                        echo "Inside deploy stage"
                    }
                }
            }
        }
}
