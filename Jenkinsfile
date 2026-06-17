pipeline{

agent any

tools{
maven 'Maven'
}
stages{
stage('Checkout'){
steps{
git branch : 'main', url : 'https://www.github.com/parsh1002/Ansible.git'
}
}
stage('Build'){
steps{
sh 'mvn clean install'
}
}
stage('Archive'){
steps{
archiveArtifacts artifacts : 'target/*.war', fingerprint:true
}
}
stage('Deploy'){
steps{
sh 'mvn clean package'
sh 'ansible-playbook ansible/playbook.yml -i ansible/hosts.ini'
}
}
}
post{
success{
echo 'Build done'
}
failure{
echo 'build failed'
}
}
}
