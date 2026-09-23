Relatório de Configuração de Rede Estática com Netplan
Disciplina: LSOR
Professor(a): Alaelson
Aluno(a): Daniel do Carmo Nascimento
Data: 23/09/2026

1. Objetivo
O objetivo desta atividade foi configurar a máquina virtual Ubuntu Server para utilizar o modo Placa em Ponte (Bridge Adapter) no VirtualBox e definir um endereço IP estático utilizando o Netplan. Também foram realizados testes de conectividade entre o computador hospedeiro Windows e a máquina virtual Ubuntu Server, além de testes de resolução de nomes e rastreamento de rotas utilizando o comando traceroute.

2. Ambiente
A atividade foi realizada utilizando o seguinte ambiente:

Item	Especificação
Sistema operacional Guest	Ubuntu Server 26.04
Sistema operacional Host	Windows 11
Plataforma de virtualização	VirtualBox
Memória RAM	2 GB
Processadores	1 vCPU
Armazenamento	32 GB
Configuração de rede inicial	NAT
Configuração de rede final	Placa em Ponte
Rede do laboratório	172.20.20.0/22
Gateway	172.20.20.1
DNS	172.20.20.1, 1.1.1.1 e 8.8.8.8
IP da VM	172.20.23.10/22
3. Procedimento
Após a configuração da placa em modo bridge e da escolha do endereço IP, foram realizados os seguintes procedimentos:

3.1 Configuração do Netplan
No Ubuntu Server, foi editado o arquivo:

sudo nano /etc/netplan/00-installer-config.yaml
Foi configurado o endereço IP estático, o gateway e os servidores DNS. Após a edição, o conteúdo foi verificado e a configuração foi aplicada. Por fim, foi verificado o endereço atribuído à interface

3.2 Testes de conectividade
Após a aplicação da configuração, foram realizados testes de comunicação entre o Windows e o Ubuntu Server.

No Windows, foi utilizado:

ping 172.20.23.10
Na máquina virtual, foi realizado o teste em direção ao endereço IP do computador hospedeiro:

ping -c 4 172.20.21.193
Também foram realizados testes de rastreamento de rota:

traceroute google.com
e:

traceroute one.one.one.one
4. Testes e Evidências

5. Conclusão
A realização desta atividade possibilitou compreender, na prática, a configuração de uma máquina virtual em modo Placa em Ponte, permitindo sua participação direta na rede física do laboratório. Também foi realizada a configuração de um endereço IP estático utilizando o Netplan, incluindo a definição da máscara de rede, gateway e servidores DNS. Dessa forma, os objetivos da atividade foram alcançados, contribuindo para a compreensão da configuração de redes estáticas e do funcionamento de máquinas virtuais conectadas diretamente a uma rede local.
