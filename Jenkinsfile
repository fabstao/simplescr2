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
              import hudson.model.Computer.ListPossibleNames

              def node = jenkins.model.Jenkins.instance.getNode( "clrvm" )
              println node.computer.getChannel().call(new ListPossibleNames())
              def slaveCIP = InetAddress.localHost.canonicalHostName
              println "Agent located at ${slaveCIP}"
              echo "Agente: ${slaveCIP}"
        }
        
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
              import hudson.model.Computer.ListPossibleNames

              def node = jenkins.model.Jenkins.instance.getNode( "ubuntuvm" )
              println node.computer.getChannel().call(new ListPossibleNames())
              def slaveUIP = InetAddress.localHost.canonicalHostName
              println "Agent located at ${slaveUIP}"
              echo "Agente: ${slaveUIP}"
              def nodes = 1
              for (int i = 0; i < nodes; ++i) {
                  echo "Testing the ${i} node ${slaveUIP}"
                 }
          }
        }
      }
    }
  }
