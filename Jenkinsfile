#!groovy

node {
         sh '''#!/bin/sh
                  toto=`helm ls --all myemp | wc -l`
                  #toto=`ls -al | wc -l`
                           if [ $toto -eq 200 ]; then
                    echo $toto equals ==== 0 ===
                  else
                    echo $toto not equal to  ==== 0 ===
                  fi
         '''
}
