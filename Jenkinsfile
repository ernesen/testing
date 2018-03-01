#!groovy

def helmInstall() {
    // Test that helm can correctly communication with the Kubernetes API
    echo "running helm test"
  	sh 'helm init'
  	sh 'helm install --name myemp myemp/'
}

def helmUpgrade() {
    // Test that helm can correctly communication with the Kubernetes API
  	sh 'helm upgrade myemp myemp/'
    sh 'helm history myemp'
}

node {
    stage('Deploy Helm') {
      sh '''
        #!/bin/sh
        
        helmVal=`helm ls --all myemp | wc -l`
     
#        if [ $helmVal -eq 0 ]; then
#          helmInstall()
#        fi
#        
#        if [ $helmVal -ne 0 ]
#        then 
#          helmUpgrade()
#        fi
      '''
    }
}
