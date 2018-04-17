stage 'Checking connectivity'

node {
    deleteDir()
    checkout scm
    
    wrap([$class: 'AnsiColorBuildWrapper', colorMapName: "xterm"]) {
        ansiblePlaybook(
            playbook: 'ping.yml',
            inventory: 'inventory.ini',
            credentialsId: '1c1789cd-36bc-4902-a275-01f57ad2f7c4',
            colorized: true)
    }
}

stage "Check syntax"

node {
    wrap([$class: 'AnsiColorBuildWrapper', colorMapName: "xterm"]) {
        ansiblePlaybook(
            playbook: 'webserver.yml',
            inventory: 'inventory.ini',
            credentialsId: '1c1789cd-36bc-4902-a275-01f57ad2f7c4',
            extras: '--syntax-check',
            colorized: true
            )
    }
}

stage "Check dry-run"

node {
    wrap([$class: 'AnsiColorBuildWrapper', colorMapName: "xterm"]) {
        ansiblePlaybook(
            playbook: 'webserver.yml',
            inventory: 'inventory.ini',
            credentialsId: '1c1789cd-36bc-4902-a275-01f57ad2f7c4',
            extras: '--check --diff',
            colorized: true
            )
    }
}

stage "Deploy to production"

node {
    wrap([$class: 'AnsiColorBuildWrapper', colorMapName: "xterm"]) {
        ansiblePlaybook(
            playbook: 'webserver.yml',
            inventory: 'inventory.ini',
            credentialsId: '1c1789cd-36bc-4902-a275-01f57ad2f7c4',
            colorized: true
            )
    }
}
