# Instalação de maquina virtual e oracle linux!
O primeiro passo para uma boa instalação, é procurar uma site confiavel, usamos o site https://www.virtualbox.org/wiki/Downloads versão 6.1 para Windows.
Logo após baixamos a iso completo do Oracle Linux(sem interface gráfica) que é o que vamos usar ao decorrer deste projeto, https://yum.oracle.com/oracle-linux-isos.html versão 8.6
Processos de instalação da máquina são simples, só dar next em tudo e iniciá-la.
Feito isso, seguimos para a criação da nossa máquina com Oracle-Linux.
# Passo a Passo dentro da máquina:

1-Clicar em novo.

2-Colocar o nome ( Oracle-Linux-Trabalho).

3- Selecionar a quantidade de memoria que a maquina terá (Dependendo da memoria do seu computador). Nesse caso 1024.

4-Tipo de arquivo rígido VDI.

5- Dinamicamente alocado.

6-Espaço da máquina-- 12 GB

7-Finaliza.

8- Antes de iniciar vamos setar as configurações.

9- Configurações - Sistema - Quantidade de processadores.

10- Armazenamento- Colocar a iso baixada, para a maquina entender que e um cd- Escolher uma imagem  de  disco
-Seleciona o Oracle-Linux.

11- Rede- Mudando do modo NAT para o modo Brigde.

12- Fianlizada configurações, podemos iniciar a máquina e instalar o linux.

13-Subindo a máquina- Seleciona o idioma- Mantemos inglês - O teclado em português(Brazil)- Disco ok.
-Placa em modo Brigde- Ethernet (enps03) ON ( já vai nos fornecer o IP, com acesso a Internet)- Senha do root ( Opcional)

14- Selecionamos a instalação mínima. (Só o necessário).

15- Iniciando a instalação..

16- Reboot do sistema - E temos a máquina. 

17- Subimos assim a máquina com o SO- Colocamos o usuário padrão e a senha.

18- Comando: IP addr para ver algumas configurações de rede.

19-Feito isso a máuina ta pronta para as configurações que deseja.

# Comunicação entre as máquinas

A comunicação entre as máquinas podem ser feitas de várias maneiras, mas nesse caso usamos o ssh, que é um protocolo de segurança, responsável por garantir que o cliente
e o servidor remoto troquem informação.
Instale o ssh na sua máquina "yum install ssh-server".
Depois verifica se está ativo "systemctl status ssh".
Faça algumas configurações se necessário.



# Comandos ssh

1- Na máquina A crie um usuário (`useradd usuario1`), define uma senha para ele (`passwd userario1`), e dê permissões para ele (`visudo`, adicione essa linha no final do arquivo: 'usuario1 ALL=(ALL) ALL').

2- Na máquina B crie um usuário (`useradd usuario2`), define uma senha para ele (`passwd userario1`), e dê permissões para ele (`visudo`, adicione essa linha no final do arquivo: 'usuario2 ALL=(ALL) ALL').

3- Na máquina B descubra o ip usando `ip a`; na máquina A use `ssh usuario2@ip` (substituia o 'ip' pelo ip da máquina B) para acessar a máquina B, execute `whoami` e se o resultado for 'usuário2' deu tudo certo, execute `exit`

4- Na máquina A descubra o ip usando `ip a`; na máquina B use `ssh usuario1@ip` (substitua o 'ip' pelo ip da máquina A) para acessar a máquina A, execute `whoami` e se o resultado for 'usuário1' deu tudo certo, execute `exit`

5- Na máquina A: `ssh-keygen -t rsa -f ~/.ssh/id_rsa` para gerar keys e `scp .ssh/id_rsa.pub usuario2@ip:/home/usuario2/.ssh/authorized_keys` (substituia 'ip' pelo ip da máquina B) para transferir a key para a máquina B.

6- Na máquina A: `ssh usuario2@ip` (substituia 'ip' pelo ip da máquina B) caso você entre sem precisar digitar a senha, deu tudo certo.

# Recomendações 

1- Usar um usuário comum com acessos root.

2-Averiguar quanto de memória sua máquina possui para que o computador suporte na hora de baixar a VM.

3-Sempre pegar link de sites oficiais.

4- Dar um systemctl restart depois de cada configuração.

5-Usar snapshosts que são feitos para guardar o estado atual da sua máquina, gerando uma imagem de estado atual. Um bom momento para criar um snapshot é sempre antes de efetuar qualquer alteração mais importante. Evitando asssim, perda de dados nos erros e insucessos dos testes.

# Links usados

1- Download e instalação do VIrtualBox.

2- Download e instalação do Oracle Linux 8.6 - sem interface gráfica.

Virtualbox download: https://www.virtualbox.org/wiki/Downloads

OracleLinux download: https://yum.oracle.com/oracle-linux-isos.html
