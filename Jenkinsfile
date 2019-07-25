pipeline {
  agent {
      node 'clrvm'
    }
  stages {
    
    stage('Clear_Test 1') {
      
      steps {
          sh '''#!/bin/bash
echo "test 1"
hostname
cat /etc/os-release
uname -a'''
          script {
              def slaveCIP = InetAddress.localHost.hostAddress
              println "Agent located at ${slaveCIP}"
      }
    }
     stage('Clear_Test 2') {
      
      steps {
          
          sh '''#!/bin/bash
echo "test 2"
hostname
cat /etc/os-release
sleep 2
uname -a'''
          sh "echo ${slaveCIP}"
      }
    }
    stage('Ubuntu_Test 1') {
       agent {
      node 'ubuntuvm'
    }
      steps {
          sh '''#!/bin/bash
echo "test UBUNTU 1"
hostname
cat /etc/os-release
sleep 2
uname -a'''
          script {
              def slaveUIP = InetAddress.localHost.hostAddress
              println "Agent located at ${slaveUIP}"
              def nodes = 1
              for (int i = 0; i < nodes; ++i) {
                  echo "Testing the ${i} node"
                 }
          }
        }
      }
    }
  }
}
