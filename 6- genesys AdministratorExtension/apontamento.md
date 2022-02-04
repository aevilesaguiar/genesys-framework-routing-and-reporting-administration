# Genesys Administrator Extension (GAX)

## Revisão: Arquitetura Genesys Administrator Extension (gax)

A imagem a seguir descreve (GAX) - uma interface de usuário associada à camada de interação do usuário - mostrada junto com suas conexões com as camadas de gerenciamento e configuração. O GAX é composto por:
- Navegador WEB
- GAX
- DAP para banco de dados GAX (DAP_JDBC)
- Banco de dados GAX


![image](https://user-images.githubusercontent.com/52088444/152529346-73efcae2-b6b1-4d48-833d-ce71d43f6f58.png)

Semelhante ao Genesys Administrator, o GAX' é um aplicativo da web. Os usuários acessam o GAX da mesma forma que o GA , via navegador da web. Suportado por Firefox Chrome e IE.

Novo na versão 8.5, o GAX agora usa uma instância JETTY incorporada como servidor de aplicativos da web; como resultado, o Tomcat não precisa mais usar o GAX. Nas versões anteriores, o GAX exigia o produto de terceiros Apache Tomcat como pré-requisito. Apache Tomcat é um servidor web e anteriormente servia o aplicativo web GAX.

GAX é cliente dos seguintes servidores e bancos de dados Genesys:

- Configuration Server - O GAX obtém objetos de configuração do Configuration Server e solicita que o Configuration Server atualize as informações de configuração com base nas tarefas que os usuários executam na interface GAX.

- Message Server - As informações de log do GAX são armazenadas no Log Database (via Message Server) e visualizadas no Genesys Administrator. Além disso, o GAX possui um recurso de auditoria que grava dados no Message Server sobre atividades no gerenciamento de parâmetros operacionais e gerenciamento de recursos de áudio, e o Message Server grava os dados no banco de dados LOG. Os usuários podem exibir dados de auditoria selecionando a opção Histórico no painel de determinados itens da interface GAX.

- Agente de controle local (LCA) e Gloval Deployment Agent (GDA) - LCA fornece informações de status sobre o GAX (se ele está em execução). GAX trabalha com GDA para implantar produtos Genesys em hosts remotos.
- Banco de dados LOG - Embora o GAX grave informações de auditoria no banco de dados LOG via Message Server (se estiver usando esse recurso), o GAX lê as informações de auditoria diretamente do banco de dados LOG.

- Banco de dados DAP para GAX - O GAX possui seu próprio banco de dados para armazenamento de informações. Associado a este banco de dados está um Database Access Point(DAP_JDBC) . Ele não depende de um DBServer para sua conexão. Em vez disso, ele usa Java Database Connection (JDBC) para fornecer os parâmetros para conexão do banco de dados.

- GAX Database - GAX armazena dados de não configuração no banco de dados GAX, como algumas informações sobre Audio Resource Management (incluindo os arquivos de recursos de áudio e personalidades), Operational Parameter Management, Solution Deployment (incluindo informações sobre pacotes de instalação) e Bulk Change Conjuntos.


## PRÉ-REQUISITOS DE TERCEIROS PARA GAX 

![image](https://user-images.githubusercontent.com/52088444/152532669-75b42c4b-1437-4e80-9b27-7ef0ab30737e.png)

https://docs.genesys.com/Documentation/GA#t-1

