pipeline {
    agent any

tools {
    checkmarx 'CheckmarxCLI'

    }

    environment {
        BRANCH_NAME = 'main'
    }

    stages {
        stage('Checkout') {
            steps {
                git branch: "${BRANCH_NAME}", url: 'https://github.com/Giuzucca/jenkins_SCM.git'
            }
        }

        stage('Checkmarx Scan') {
            steps {
                checkmarxASTScanner(
                    additionalOptions: '--scan-types sast',
                    baseAuthUrl: 'https://iam.checkmarx.net',
                    branchName: "${BRANCH_NAME}",
                    checkmarxInstallation: 'CheckmarxCLI',
                    credentialsId: 'CX_ID_JENKINS',
                    projectName: 'teste_jenkins_SCM',
                    serverUrl: 'https://eu.ast.checkmarx.net',
                    tenantName: 'nova_beta8'
                )
            }
        }
    }

    post {
        always {
            echo 'Pipeline finalizado.'
        }
    }
}
