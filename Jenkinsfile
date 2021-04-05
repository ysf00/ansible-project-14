pipeline {
    agent any

    parameters {
      string(name: 'inventory_file', defaultValue: 'dev',  description: 'This is the inventory file for the environment to deploy configuration')
      string(name: 'limit_inventory_group', defaultValue: '',  description: 'This is a group from the inventory file')
      string(name: 'ansible_tag', defaultValue: '', description: 'Ansible tag to only run specific tasks')
    }

 environment {
      // JENKINS_SSH_PRIVKEY="~/.ssh/jenkins.pem"
      JENKINS_KUBE_CONFIG_FILE="~/.kube/config"
      JENKINS_ANSIBLE_CFG_FILE="${WORKSPACE}/playbooks/ansible.cfg"
      ANSIBLE_FORCE_COLOR="true"
      DEFAULT_PRIVATE_KEY_FILE="~/.ssh/jenkins.pem"
    }

    stage('Checkout')
        {
        steps {
        checkout([
            $class: 'GitSCM', 
            doGenerateSubmoduleConfigurations: false, 
            extensions: [],
            submoduleCfg: [], 
            branches: [[name: 'develop']],
            userRemoteConfigs: [[url: "https://gitlab.com/zooto.io/ansible.git",credentialsId:'GIT_CREDENTIALS']]
            ])
                }
          }                   


}
