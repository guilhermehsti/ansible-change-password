# ansible-change-password
Role criada para alteração em massa da senha de usuário em servidores linux utilizando Ansible. Foram realizados testes em distribuiçoes debian e ubuntu

1. Pré-requisitos: 
  a) instalar pacote sudo nos hosts que ainda não está com pacote instalado, para elevação de privilégios
  b) instalar o pacote newpass para gerar senha aleatória durante execução da task. Comando: sudo snap install newpass

2. Estrutura:
  a) arquivos utilizados durante a execução da role:
ansible.cfg ##configurações padrões do ambiente
group_vars > onpremise > vars 
##variáveis utilizadas para todos os hosts adicionados ao grupo onpremise
hosts ##declaração dos targets e grupos
playbook.yml ##declaração da role que será executada e de hosts/grupos onde serão executadas as tasks.
roles > alteracao_senha > tasks > main.yml ##lista de tarefas a serem executas na role

3. Execução: 
  a) Para executar a task, é necessário o seguinte comando: ansible-playbook -i hosts playbook.yml --extra-vars="name_user=usuario" -K
  ##com a opção --extra-vars, a variável name_user recebe o argumento com o nome do usuário que deverá ter a senha alterada.##
  ##a opção -K irá pedir a senha sudo para eleveçao de privilégios. ##
  ##o arquivo com as senhas geradas será salvo no localhost em $HOME ##
