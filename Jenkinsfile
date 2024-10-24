node {
    def app
    stage('Clone repository') {
        git 'https://github.com/20211130/fork_vs_vfork.git'
    }
    stage('Build image') {
        app = docker.build("yejin20211130/test")
    }
    stage('Test image') {
        app.inside {
            sh 'make test'
        }
    }
    stage('Push image') {
        docker.withRegistry('https://registry.hub.docker.com', 'yejin20211130') {
           app.push("${env.BUILD_NUMBER}")
           app.push("latest")
        }
    }
}
