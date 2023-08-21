node {
    
    stage('Preparation') {
        checkout scm
        sh "git rev-parse --short HEAD > .git/commit-id"
        commit_id = readFile('.git/commit-id').trim()
    }
    
    stage('Deploy') {
        def myTestContainer = docker.image('node:4.6')
        
        myTestContainer.pull()
        myTestContainer.inside {
            sh 'npm install --only=dev'
            sh 'npm start'
        }
    }

}