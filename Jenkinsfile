#!groovy

node {

    steps {
         bash '''#!/bin/bash
                 echo "hello world"
                 toto=`helm ls --all myemp | wc -l`
                 echo $toto
                 
         '''
    }

}
