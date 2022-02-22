# Routing Serves

O roteamento é composto de:

- Composer
-  Web application Server (ORS)
- uNIVERSAL rOUTING sERVER(urs)

## Conections

O URS e o ORS devem estar conectados aos mesmos T-servers para que possam se registrar para Números de Diretório e receber mensagens sobre atividade e ter a mesma lista
de locatários(tenants).


URS e ORS devem estar conectados ao configuration Server  para saber sobre sua própria configuração.

O URS deve estar conectado ao Stat Server para monitorar os agentes para fins de roteamento, o que inclui: O status dos agentes disponíveis para roteamento e a 
estatística para escolha entre eles (o melhor agente para fins de roteamento), etc.

O ORS deve estar conectado para ser servidor de aplicação web (the application Server)para obter o arquivo SCXML criado no Composer, que contém a lógica desejada para roteamento.

![image](https://user-images.githubusercontent.com/52088444/155157543-82ab83ec-d9f2-4b73-802f-900228e4794f.png)

## Sobre o servidor de orquestração

O Orchestration Server (ORS) pega o recurso central de roteamento da Genesys e o estende, generaliza e o integra mais firmemente a outros produtos da Genesys.
A orquestração fornece gerenciamento dinâmico de interações por meio do uso de ferramentas de regras de negócios, dados dinâmicos e aplicativos baseados em padrões abertos.

A orquestração fornece gerenciamento dinâmico de interações por meio do uso de ferramentas de regras de negócios, dados dinâmicos e aplicativos baseados em padrões
abertos (por exemplo, aplicativos de roteamento baseados em SCXML criados no Composer ).

## Capacidades ORS
Abaixo está um exemplo de interação com o cliente que envolve várias sessões espalhadas ao longo do tempo.

Um cliente do banco liga para um número 800 para perguntar sobre a pré-aprovação de hipoteca. Uma resposta de voz interativa (IVR) solicita que ele insira o número de sua conta e o transfere para um agente.
O agente preenche um formulário para o cliente e pede-lhe que envie por fax alguns documentos comprovativos.
Depois que o cliente envia os documentos por fax, ele recebe uma mensagem SMS automática, que agradece e informa que receberá uma resposta em 48 horas.
Dentro de um ou dois dias, o cliente recebe um e-mail parabenizando-o pela aprovação de sua inscrição.
Este exemplo, envolvendo canais de voz, URA, fax, SMS e e-mail, mostra como o ORS é capaz de tratar todas as diversas transações como um único serviço.

## Orquestrando o Atendimento ao Cliente
O Orchestration Server recebe esse nome por sua capacidade de "orquestrar" (direcionar e controlar) os serviços ao cliente. Os aplicativos de roteamento/atendimento 
ao cliente ORS podem processar:

- Através de várias interações com um cliente.
- Através de vários canais para interagir com um cliente.
- Aplicativos integrados e consistentes com os processos de negócios de uma organização.
O ORS pode trabalhar com vários tipos de aplicativos, como estratégias de roteamento, lógica de sessão, lógica de serviço e lógica de estado de serviço da interação.


## Baseado em SCXML

A adição de ORS ao roteamento universal permite uma abordagem aberta para a criação de estratégias de roteamento:

- Antes do ORS, o URS executava estratégias de roteamento criadas no Interaction Routing Designer usando a Genesys Interaction Routing Language (IRL) proprietária.
- Por outro lado, o ORS pode executar estratégias de roteamento e aplicativos criados no Composer escritos em uma linguagem aberta e não proprietária: SCXML.

O ORS pode lidar com ambientes de voz pura, sem voz e multimídia, permitindo o roteamento de cada tipo de mídia com base em critérios apropriados. 
As estratégias de roteamento e os processos de negócios automatizam o roteamento de interação para o agente/recurso mais apropriado com base em fatores como 
o tipo de consulta, o valor comercial da interação com o cliente, o contexto e o perfil do cliente e o canal de mídia.


