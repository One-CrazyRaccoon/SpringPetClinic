node {
    def mvnHome = tool name: 'M3', type: 'maven'

    stage('Checkout') {
        git url: 'https://github.com/One-CrazyRaccoon/SpringPetClinic/', branch: 'main'
    }

    stage('Compile') {
        bat "\"${mvnHome}\\bin\\mvn\" compile"
    }

    stage('Test') {
        bat "\"${mvnHome}\\bin\\mvn\" test -Djacoco.skip=true"
    }

    stage('Package') {
        bat "\"${mvnHome}\\bin\\mvn\" package -DskipTests"
    }

    stage('Deploy') {
        bat "javaw -jar target\\spring-petclinic-2.1.0.BUILD-SNAPSHOT.jar --server.port=8081"
    }
}
