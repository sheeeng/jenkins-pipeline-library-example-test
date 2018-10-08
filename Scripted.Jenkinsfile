#!/usr/bin/env groovy

@Library('deadly-viper-library')
import org.contoso.WesterosFolks

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
