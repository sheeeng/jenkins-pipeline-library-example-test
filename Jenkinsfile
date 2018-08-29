@Library('deadly-viper-library')
import org.contoso.WesterosFolks

import hudson.model.*
def env = build.getEnvironment()
def gitBranch = env['GIT_BRANCH']
def gitCommit = env['GIT_COMMIT']
def shortGitCommit = gitCommit[0..6]
def gitPreviousCommit = env['GIT_PREVIOUS_COMMIT']
def gitPreviousSuccessfulCommit = env['GIT_PREVIOUS_SUCCESSFUL_COMMIT']
sh 'echo ${gitBranch}'
sh 'echo ${gitCommit}'
sh 'echo ${shortGitCommit}'
sh 'echo ${gitPreviousCommit}'
sh 'echo ${gitPreviousSuccessfulCommit}'

node {
    stage('Main') {
        try {
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
