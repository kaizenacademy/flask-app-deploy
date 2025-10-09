template = '''
apiVersion: v1
kind: Pod
metadata:
  labels:
    run: kubernetes
  name: kubernetes
spec:
  containers:
  - image: kaizenacademy/my-binary:1.0.0
    name: kubernetes
    '''

podTemplate(cloud: 'kubernetes', label: 'kubernetes', yaml: template) {
node("kubernetes") {
    container("kubernetes") {
    stage("Checkout SCM") { 
        git branch: 'main', url: 'https://github.com/kaizenacademy/flask-app-deploy.git'
    } 

    stage("Check") {
        sh """
        terraform version
        helm version
        kubectl version
        kubectl get nodes
        """
    }
    }
}
}