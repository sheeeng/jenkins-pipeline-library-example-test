@Library('deadly-viper-library')
import org.contoso.WesterosFolks

node {
    stage('Main') {
        try {
            abortPreviousBuilds()
            sh 'env | sort'
            // https://issues.jenkins-ci.org/browse/JENKINS-46285
            sh "echo ${env.BUILD_URL}"
            sh "echo ${env.GIT_BRANCH}"
            sh "echo ${env.GIT_COMMIT}"
            sh "echo ${env.GIT_COMMIT}[0..6]"
            sh "echo ${env.GIT_PREVIOUS_COMMIT}"
            sh "echo ${env.GIT_PREVIOUS_SUCCESSFUL_COMMIT}"
            sleep 42
        }
        catch (e) {
            echo 'Uh oh! What happened?'
            throw e
        }
    }
}
