node("static_ansible"){
    stage("Help message"){
        echo "Debug: "
        echo "Release: ansible_docker"
    }
    stage("Git checkout"){
        git credentialsId: '5ac0095d-0185-431b-94da-09a0ad9b0e2c', url: 'git@github.com:aragastmatb/example-playbook.git'
    }
    stage("Check ssh key"){
        secret_check=true
    }
    stage("Run playbook"){
        if (secret_check){
            withCredentials([usernamePassword(credentialsId: 'mycreds', usernameVariable: 'USERNAME', passwordVariable: 'PASSWORD')]) {
                 sh 'ansible-playbook site.yml -i inventory/prod.yml --extra-vars ansible_sudo_pass=$PASSWORD'
           }
        }
        else{
            echo 'no more keys'
        }
        
    }
}
