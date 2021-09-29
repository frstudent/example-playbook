node("ansible_docker"){
    stage("Help message"){
        echo "Debug: static_ansible"
        echo "Release: ansible_docker"
    }
    stage("Git checkout"){
        git credentialsId: 'cb0b173c-2e3b-466f-b570-cacc58d05021', url: 'git@github.com:frstudent/example-playbook.git'
    }
    stage("Check ssh key"){
        secret_check=true
    }
    stage("Run playbook"){
        if (secret_check){
            withCredentials([usernamePassword(credentialsId: 'a0f1679b-ac18-40c0-bfb8-7cbd55f74abb', usernameVariable: 'USERNAME', passwordVariable: 'PASSWORD')]) {
                 // echo '$PASSWORD'
                 sh 'ansible-playbook site.yml -i inventory/prod.yml --extra-vars ansible_sudo_pass=$PASSWORD'
           }
        }
        else{
            echo 'no more keys'
        }
        
    }
}
