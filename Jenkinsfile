@Library('deadly-viper-library')
import org.contoso.WesterosFolks

node {
    stage('Main') {
        try {
            abortPreviousBuilds()
            sh 'env | sort'
            sh 'echo ${GIT_BRANCH}'
            sh 'echo ${GIT_COMMIT}'
            sh 'echo ${GIT_COMMIT}[0..6]'
            sh 'echo ${GIT_PREVIOUS_COMMIT}'
            sh 'echo ${GIT_PREVIOUS_SUCCESSFUL_COMMIT}'
            sleep 42
        }
        catch (e) {
            echo 'Uh oh! What happened?'
            throw e
        }
    }
}
