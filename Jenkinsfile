stage 'Checking connectivity'

node {
    deleteDir()
    checkout scm
    
    wrap([$class: 'AnsiColorBuildWrapper', colorMapName: "xterm"]) {
        ansiblePlaybook(
            playbook: 'ping.yml',
            inventory: 'inventory.ini',
            credentialsId: '9be9c47b-9518-47bb-b8e7-8f56d1b6d414',
            colorized: true)
    }
}

stage "Check syntax"

node {
    wrap([$class: 'AnsiColorBuildWrapper', colorMapName: "xterm"]) {
        ansiblePlaybook(
            playbook: 'webserver.yml',
            inventory: 'inventory.ini',
            credentialsId: '9be9c47b-9518-47bb-b8e7-8f56d1b6d414',
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
            credentialsId: '9be9c47b-9518-47bb-b8e7-8f56d1b6d414',
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
            credentialsId: '9be9c47b-9518-47bb-b8e7-8f56d1b6d414',
            colorized: true
            )
    }
}
