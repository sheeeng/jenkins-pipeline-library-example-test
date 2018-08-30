@Library('deadly-viper-library')
import org.contoso.WesterosFolks

node {
    stage('Main') {
        try {
            getTriggerCauses()
            abortPreviousBuilds()
            sh 'env | sort'
            // https://issues.jenkins-ci.org/browse/JENKINS-46285
            sh "echo ${env.BUILD_URL}"
            sh "echo ${env.BUILD_NUMBER}"
            sh "echo ${env.GIT_COMMIT}"
            sleep 42
        }
        catch (e) {
            echo 'Uh oh! What happened?'
            throw e
        }
    }
}
