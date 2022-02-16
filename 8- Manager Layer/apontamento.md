# Management Layer (Camada de Gerenciamento)

A Camada de Gerenciamento fornece uma espécie de "controle de missão" centralizado e é responsável pelo Controle de Soluções, Processamento de Alarmes e Tratamento de Falhas.

(The Management Layer provides a kind of centralized "mission control" and is responsible for the Solution Control, Alarm Processing , and Fault Handlin.)

## The Management Layer Architecture(A Arquitetura da Camada de Gerenciamento)

O seguinte descreve a camada de gerenciamento - mostrada em detalhes - juntamente com suas conexões com as camadas de interação e configurações do usuário. A camada de gerenciamento é composta por:

- Servidor de mensagens(Message Server) - T
- Ponto de acesso de banco de dados ( Database Access Point-DAP)
- Banco de dados de registros(Log Database)
- Servidor de Controle da Solução(Solution Controle Server)
- Agente de Controle Local(Local Control Agent)
- Agente de implantação Genesys(Genesys Deployment Agent)

![image](https://user-images.githubusercontent.com/52088444/154311327-4afad2bd-8429-46c6-9acd-4abecb292ac9.png)

