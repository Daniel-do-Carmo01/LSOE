# Relatório de Configuração de Gateway NAT com IPTables

> **Disciplina:** LSOR 
> **Professor(a):** Alaelson
> **Aluno(a):** Daniel do Carmo Nascimento
> **Data:** 30/09/2026 

## 1. Objetivo
O objetivo desta atividade foi configurar um servidor Ubuntu como **Gateway de Rede**, permitindo a comunicação entre uma rede interna e uma rede externa 
por meio de roteamento e NAT utilizando IPTables.
Durante a prática, foram configuradas duas máquinas virtuais, sendo uma responsável pelo encaminhamento dos pacotes e outra utilizada como cliente da rede interna.
Também foram realizados testes de conectividade para verificar o acesso à rede externa e à internet, que ainda não funciona corretamente.

## 2. Ambiente
A atividade foi realizada utilizando o seguinte ambiente:

| Item | Especificação |
|---|---|
| Sistema operacional | Ubuntu Server 26.04 |
| Plataforma de virtualização | VirtualBox |
| Computador hospedeiro | Windows 11 |
| Memória RAM | 2 GB por VM |
| Processadores | 1 vCPU por VM |
| Armazenamento | 32 GB por VM |
| VM1 | Gateway / Roteador |
| VM2 | Cliente da rede interna |
| Interface externa da VM1 | Bridge (enp0s3) |
| Interface interna da VM1 | Rede Interna (enp0s8) |
| Interface da VM2 | Rede Interna (enp0s3) |

### 3. Endereçamento de rede

| Equipamento | Interface | Endereço IP |
|---|---|---|
| VM1 (Gateway) | enp0s3 | 172.20.23.10/22 |
| VM1 (Gateway) | enp0s8 | 10.0.0.1/24 |
| VM2 (Cliente) | enp0s3 | 10.0.0.2/24 |
| Gateway externo | - | 172.20.20.1 |

## 4. Procedimento
### 4.1 Configuração das interfaces de rede
Inicialmente, foram configurados os adaptadores de rede das duas máquinas virtuais no VirtualBox. A VM1 recebeu duas interfaces: uma em modo Placa em Ponte (Bridge)
e outra em Rede Interna. A VM2 foi configurada utilizando apenas a Rede Interna, com o mesmo nome definido na VM1.

### 4.2 Configuração do Netplan na VM1 e VM2

Na VM1 foi editado o arquivo de configuração do Netplan, configurando as interfaces externa e interna, utilizando os endereços IP definidos para a topologia.
Já na VM2, foi configurado o endereço IP `10.0.0.1/24`, utilizando a VM1 (`10.0.0.2`) como gateway padrão.

## 5. Testes e Evidências
**Figura 1 – Configuração de rede da VM1 e VM2**
<img width="643" height="275" alt="Captura de tela 2026-10-07 212202" src="https://github.com/user-attachments/assets/1ff200de-07ec-4f45-932c-e17a96a8b7cc" />
<img width="636" height="276" alt="vm2" src="https://github.com/user-attachments/assets/5679fa7b-659d-4d6f-9f29-7d72a05a77a5" />
<img width="635" height="272" alt="vm1" src="https://github.com/user-attachments/assets/9971a63d-fb14-410d-90fe-7d43dc77b94c" />


**Figura 2 – Saída do dos Arquivos Netplan**
<img width="879" height="379" alt="Captura de tela 2026-10-07 213453" src="https://github.com/user-attachments/assets/1f9ff0f2-242c-4090-9f8e-5492fbf77ce4" />
<img width="835" height="294" alt="Captura de tela 2026-10-07 213810" src="https://github.com/user-attachments/assets/158f7f6a-5599-4c33-85da-d203fd613975" />


**Figura 3 – Print dos Testes de Ping na VM1:** <br>
<img width="523" height="198" alt="Captura de tela 2026-10-02 081541" src="https://github.com/user-attachments/assets/35ed98d6-b166-4414-8294-2b4b80ea0e44" />

**Figura 4 – Comunicação entre VM2 e VM1** <br>
<img width="562" height="200" alt="Captura de tela 2026-10-02 081603" src="https://github.com/user-attachments/assets/59031218-56ab-4b0f-84f0-a6a0f6beda65" />

**Figura 5 – Teste de conectividade com a rede externa e internet**
<img width="558" height="247" alt="Captura de tela 2026-10-02 082045" src="https://github.com/user-attachments/assets/d7156371-c652-44df-90b6-a8dfa74aef88" />

Estes testes não funcionaram, pois não foi criada uma NAT.

**Figura 6 – Traceroute para domínio externo** <br>
Não foi possível executar este teste, pois a máquina não tem acesso a rede para baixar o pacote necessário (traceroute).

## 6. Problemas e Soluções
### 6.1 Problemas de conectividade entre as máquinas virtuais
Devido a ausência da habilitação do encaminhamento IPv4 ou de regras adequadas no IPTables não foi possível permitir que a VM2 acesse a rede externa.

## 7. Conclusão
A realização desta atividade possibilitou compreender, na prática, o funcionamento de um servidor Linux como Gateway de Rede, utilizando duas interfaces de rede para conectar uma rede interna a uma rede externa.
Os testes de conectividade e rastreamento de rotas permitiram verificar a necessidade de uma NAT para a comunicação entre as máquinas virtuais.
