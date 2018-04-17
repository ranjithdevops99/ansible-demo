stage 'Checking connectivity'

node {
    deleteDir()
    checkout scm
    
    wrap([$class: 'AnsiColorBuildWrapper', colorMapName: "xterm"]) {
        ansiblePlaybook(
            playbook: 'ping.yml',
            inventory: 'inventory.ini',
            credentialsId: '/root/.ssh/id_rsa',
            colorized: true)
    }
}

stage "Check syntax"

node {
    wrap([$class: 'AnsiColorBuildWrapper', colorMapName: "xterm"]) {
        ansiblePlaybook(
            playbook: 'webserver.yml',
            inventory: 'inventory.ini',
            credentialsId: '8660dc0b-c062-49c6-ac26-b6c0856f47f8',
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
            credentialsId: '8660dc0b-c062-49c6-ac26-b6c0856f47f8',
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
            credentialsId: '8660dc0b-c062-49c6-ac26-b6c0856f47f8',
            colorized: true
            )
    }
}
