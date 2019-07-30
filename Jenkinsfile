pipeline {
  agent {
      node 'clrvmk8s'
    }
  stages {
    
    stage('Install K8s Master') {
      
      steps {
          sh '''#!/bin/bash
whoami
curl https://gitlab.devtools.intel.com/snippets/536/raw > envs.sh
source envs.sh
sudo swupd bundle-add cloud-native-basic
sudo mv /usr/share/clr-k8s-examples/kubeadm.yaml /usr/share/clr-k8s-examples/kubeadm.yaml.old
nopr
sudo curl https://gitlab.devtools.intel.com/snippets/538/raw > /usr/share/clr-k8s-examples/kubeadm.yaml
cd /usr/share/clr-k8s-examples
sudo ./setup_system.sh
sudo ./create_stack.sh <<EOF

EOF
'''
          script {
              def MasterHostname = InetAddress.localHost.canonicalHostName
              println "Master k8s Agent located at ${MasterHostname}"
              def masterIP = "ip a | awk '/inet6|127/ {next;} /inet/ {print \$2}' | sed 's/\/[0-9][0-9]//g'".execute().text
              echo "Master Agent: ${masterIP}"
        }
        
     }
    }
     stage('Clear_Test task 1') {
      
      steps {
          
          sh '''#!/bin/bash
echo "test 2"
hostname
cat /etc/os-release
sleep 2
uname -a'''
      }
    }
    stage('Join K8s worker - ClearLinux') {
       agent {
      node 'clrvmk8s'
    }
      steps {
          sh '''#!/bin/bash
whoami
curl https://gitlab.devtools.intel.com/snippets/536/raw > envs.sh
source envs.sh
sudo swupd bundle-add cloud-native-basic
cd /usr/share/clr-k8s-examples
sudo ./setup_system.sh'''
          script {
              def slaveIP = "ip a | awk '/inet6|127/ {next;} /inet/ {print \$2}' | sed 's/\/[0-9][0-9]//g'".execute().text
              echo "Worker Agent: ${slaveIP}"
            def joinlog = "sudo kubeadm join ${masterIP}:6443 --token v1un4v.4c4v3st1d4d3un1f --discovery-token-unsafe-skip-ca-verification".execute().text
          }
        }
      }
    }
  }
