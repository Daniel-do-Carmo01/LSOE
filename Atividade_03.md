# Relatório Técnico - Aula Prática 03
## 1. Identificação
Título da prática: Estrutura de Diretórios, FHS e Permissões Avançadas no Linux Server
Aluno: Daniel do Carmo Nascimento
Matrícula: 2023011920
Turma: LSOR - BSI
Data da prática: 25/08/2026
## 2. Objetivo
Explorar diretórios fundamentais do sistema Linux segundo o padrão FHS, criar estruturas departamentais sob /srv, associar grupos a essas estruturas e validar o isolamento de acesso entre usuários de diferentes setores.

## 3. Ambiente
Sistema operacional: Ubuntu Server 26.04 LTS
Ambiente de execução: máquina virtual criada na Aula 1
Usuário administrativo utilizado: administrador
Diretórios criados na prática: /srv/ti-dept, /srv/ti-dept/projetos, /srv/vendas-dept, /srv/vendas-dept/relatorios e /srv/diretoria-dept
Grupos utilizados: ti-group, vendas-group e diretoria-group
Usuários envolvidos nos testes: fulano, cicrano e beltrano
## 4. Procedimento
Foi feita a navegação até /etc, seguida de listagem parcial do conteúdo e verificação do diretório atual com pwd.
Foi consultado o arquivo de log /var/log/auth.log para visualizar eventos recentes de autenticação e uso de sudo.
No diretório /srv, foram criadas de forma recursiva as estruturas ti-dept/projetos e vendas-dept/relatorios com mkdir -p.
Foram criados os grupos ti-group e vendas-group.
O usuário fulano foi adicionado ao grupo ti-group, e o usuário cicrano foi adicionado ao grupo vendas-group.
As pastas departamentais inicialmente pertencentes a root:root tiveram sua posse alterada para administrador:ti-group e administrador:vendas-group.
Foram aplicadas permissões 770 nas duas pastas principais, garantindo acesso apenas ao administrador e ao grupo correspondente.
A posse das estruturas internas também foi ajustada de forma recursiva.
Foi criado o arquivo arquitetura_rede_vpn.txt em /srv/ti-dept/projetos, com posse administrador:ti-group e permissão 660.
No teste de validação, fulano conseguiu acessar /srv/ti-dept e listar o arquivo do seu departamento.
Em contrapartida, cicrano recebeu Permission denied ao tentar acessar a pasta de Tecnologia.

## Fotos adicionadas nas pastas.
