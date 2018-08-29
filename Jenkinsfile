@Library('deadly-viper-library')
import org.contoso.WesterosFolks

node {
    stage('Main') {
        try {
            def env = build.getEnvironment()
            def gitBranch = env['GIT_BRANCH']
            sh 'echo ${gitBranch}'
            def gitCommit = env['GIT_COMMIT']
            sh 'echo ${gitCommit}'
            def shortGitCommit = gitCommit[0..6]
            sh 'echo ${shortGitCommit}'
            def gitPreviousCommit = env['GIT_PREVIOUS_COMMIT']
            sh 'echo ${gitPreviousCommit}'
            def gitPreviousSuccessfulCommit = env['GIT_PREVIOUS_SUCCESSFUL_COMMIT']
            sh 'echo ${gitPreviousSuccessfulCommit}'
            
 
            abortPreviousBuilds()
            sh 'env | sort'
            sleep 42
        }
        catch (e) {
            echo 'Uh oh! What happened?'
            throw e
        }
    }
}
