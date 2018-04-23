stage 'Checking connectivity'

node {
    deleteDir()
    checkout scm
    
    wrap([$class: 'AnsiColorBuildWrapper', colorMapName: "xterm"]) {
        ansiblePlaybook(
            playbook: 'ping.yml',
            inventory: 'inventory.ini',
            credentialsId: '353e340f-3a35-4695-965d-1bcfc2cb7591',
            colorized: true)
    }
}

stage "Check syntax"

node {
    wrap([$class: 'AnsiColorBuildWrapper', colorMapName: "xterm"]) {
        ansiblePlaybook(
            playbook: 'webserver.yml',
            inventory: 'inventory.ini',
            credentialsId: '353e340f-3a35-4695-965d-1bcfc2cb7591',
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
            credentialsId: '353e340f-3a35-4695-965d-1bcfc2cb7591',
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
            credentialsId: '353e340f-3a35-4695-965d-1bcfc2cb7591',
            colorized: true
            )
    }
}
