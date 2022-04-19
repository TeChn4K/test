podTemplate(
  serviceAccount: "jenkins", 
  containers: [
    // containerTemplate(name: 'shell', image: 'alpine:3.14', command: 'sleep', args: '99d'),
    // containerTemplate(name: 'kaniko', image: 'gcr.io/kaniko-project/executor:debug', command: 'sleep', args: '99d', ttyEnabled: true),
    // containerTemplate(name: 'kustomize', image: 'eu.gcr.io/k8s-artifacts-prod/kustomize/kustomize:v4.5.4', command: 'sleep', args: '99d', ttyEnabled: true),
    containerTemplate(name: 'kubectl', image: 'lachlanevenson/k8s-kubectl:v1.23.4', command: 'sleep', args: '99d', ttyEnabled: true),
  ]
) {

  node(POD_LABEL) {
    stage('Git') {
      checkout scm
    }

    // stage('Build') {
    //   container('kaniko') {
    //     sh '/kaniko/executor -f "`pwd`/Dockerfile" -c "`pwd`" --destination=nginx-myhello:latest --no-push' 
    //   }
    // }

    stage('K8s') {
      container('kubectl') {
        sh 'kubectl get pods'
      }
    }

    // stage('stage1') {
    //   container('shell') {
    //     sh 'hostname'
    //     sh 'cat /etc/os-release'
    //   }
    // }
  }
}

