# Frameworks Connections (Conexões de estrutura)

![image](https://user-images.githubusercontent.com/52088444/155138216-46bdf132-1399-46c3-b830-4df851fc02e0.png)

## Configuration Layer

**Genesys Administrator(GA) :** O componente User Interaction Layer baseado na Web que fornece uma interface para a Camada de Configuração (Configuration Layer),
Camada de Gerenciamento(Management Layer,) e outras soluções da Genesys.

**Configuration Server**: - O componente Genesys Framework que armazena e gerencia dados do banco de dados de configuração(Configuration Database) , que os usuários 
acessam por meio do Configuration Manager e do Genesys Administrator. O Configuration Server impede a entrada de dados de configuração logicamente incorretos, permite o 
controle de acesso aos dados baseado em privilégios do usuário e notifica os aplicativos cliente dinamicamente sobre as alterações feitas nos dados.

**Configuration Database:** O banco de dados que armazena todas as informações de configuração de um contact center.

**Genesys Administrator Extension(GA)**: Também conhecido como GAX, o Genesys Administrator Extension é um componente da camada de interação (Interactio Layer) do usuário 
baseado na Web que fornece interfaces amigáveis para ajudar os usuários a realizar operações complexas e, ao mesmo tempo, evitar erros do usuário. O GAX fornece uma interface
para a Camada de Configuração(Configuration Layer), Camada de Gerenciamento(Managment Layer) e outras soluções da Genesys.

## Managment Layer

**Local Control Agent (LCA):** Também conhecido como LCA. Um componente daemon da camada de gerenciamento que controla todos os aplicativos daemon que estão sendo executados
no Genesys Framework . Um módulo de software fornecido pela Genesys que é carregado em cada plataforma de servidor que hospeda um ou mais módulos de servidor Genesys.
O objetivo do LCA é monitorar o status operacional de todos os módulos de software Genesys em execução localmente, relatar erros e reiniciar os módulos se eles pararem de 
funcionar.

**Solution Control Server(SCS):** Também conhecido como SC. O componente Genesys Framework que serve como ponto de controle para o qual o SCI é a interface. Juntos,
SCS e SCI fornecem os serviços descritos na definição de SCI.

**Solution Control Interface:** Também conhecido como SCI. Um componente do Genesys Framework que é usado para administrar soluções Genesys—por exemplo, para iniciar
ou parar a solução, visualizar logs, configurar alarmes acionados por eventos e fornecer informações de status em tempo real para todos os aplicativos Genesys.

**Message Server:** O componente Genesys Framework que fornece processamento e armazenamento centralizado de eventos de manutenção de cada aplicativo. Os eventos 
são armazenados como registros de log no banco de dados de log centralizado, onde ficam disponíveis para processamento centralizado adicional. O Message Server 
também pode ser configurado para produzir mensagens de saída (alarmes) que são acionadas por eventos de log configurados. Se detectar uma correspondência, 
ele envia o alarme para o Solution Control Server para processamento imediato.

## User Interaction Layer 
Atualmente, o Genesys Administrator e sua extensão(GAX é o único componente na camada User Interaction.

## Media Layer

**T-Server:** O componente de software Genesys que fornece uma interface entre seu hardware de telefonia e o restante dos componentes de software Genesys em sua empresa. 
Ele traduz e mantém o controle de eventos e solicitações que vêm e são enviados para o link Computer-Telephony Integration (CTI) no dispositivo de telefonia. 
T-Server é um servidor baseado em TCP/IP que também pode atuar como uma interface de mensagens entre clientes T-Server. É o ponto crítico para permitir que sua
solução Genesys facilite e rastreie os contatos que fluem pela sua empresa.

## Services Layer

**Stat Server:** O Stat Server é um aplicativo da Genesys que rastreia informações sobre redes de interação com o cliente (contact center, telefonia corporativa ou 
redes de computadores e redes de computadores). O Stat Server também converte os dados acumulados para números de diretório (DNs), agentes, grupos de agentes e tipos 
de objetos não específicos de telefonia, como e-mail e sessões de bate-papo, em informações estatisticamente úteis e passa esses cálculos para outros aplicativos de 
software que solicitam dados. Por exemplo, o Stat Server envia dados ao Universal Routing Server (URS) para informar o URS sobre a disponibilidade do agente. 
Você também pode usar os valores estatísticos numéricos do Stat Server como critérios de roteamento. O Stat Server fornece aos gerentes de contact center uma 
ampla gama de informações, permitindo que as organizações maximizem a eficiência e a flexibilidade das redes de interação com o cliente.



