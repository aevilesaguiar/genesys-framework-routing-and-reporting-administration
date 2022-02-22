# Arquitetura Genesys Framework

O Genesys Framework consiste em cinco camadas . Em configurações sofisticadas usando a funcionalidade da Camada de Gerenciamento, cada camada depende 
das camadas abaixo dela para funcionar corretamente.
![image](https://user-images.githubusercontent.com/52088444/155136655-6099babc-3206-4398-b956-e23c9ab5c76f.png)

## Configuration Layer:
A Camada de Configuração(Configuration Layer) processa e armazena todos os dados necessários para executar as soluções Genesys em 
um ambiente específico; ele notifica os clientes sobre quaisquer alterações de configuração. A Camada de Configuração também controla o acesso do usuário às 
funções e dados de uma solução.

**O configuration Layer fornece:**
•	Processamento e armazenamento de dados de configuração centralizados para entrada única de qualquer informação sobre entidades de contact center que qualquer
número de aplicativos requer para funcionar em um ambiente de negócios específico. Qualquer número de aplicativos pode usar essas informações.
•	Um mecanismo avançado de distribuição de dados de configuração, para que os aplicativos possam ler sua configuração na inicialização e serem notificados sobre 
atualizações em tempo de execução sem interrupções de serviço.
•	Funções abrangentes de controle de integridade de dados que impedem a entrada de dados de configuração ilógicos que podem causar mau funcionamento da solução.
•	Gerenciamento avançado de reconexão que garante que os aplicativos tenham dados atualizados após o restabelecimento da conexão com o Configuration Server.
•	Funções de controle de acesso para regular o acesso do usuário às funções e dados da solução, com base nos privilégios de acesso definidos para cada item.
•	Assistentes para ajudar os usuários no processo automatizado de implantação da solução.
•	Suporte para ambientes distribuídos geograficamente.
•	Integração com fontes de dados externas, das quais você pode importar dados de configuração para o Banco de Dados de Configuração.
•	Importação e exportação de dados de configuração de e para o banco de dados de configuração.
•	Transferência segura de dados entre componentes Genesys usando o protocolo Transport Layer Security (TLS).

## Managment Layer: A camada de gerenciamento(Management Layer) 
controla a inicialização e o status das soluções, registro de eventos de manutenção, geração e processamento de 
alarmes e gerenciamento de falhas de aplicativos.

**A camada de gerenciamento fornece:**

•	Controle e monitoramento centralizado da solução, exibindo o status em tempo real de cada objeto Solution configurado e ativando e desativando soluções e aplicativos
únicos, incluindo soluções definidas pelo usuário.
•	Log centralizado que registra eventos de manutenção de aplicativos. O formato de log unificado permite a fácil seleção de registros de log necessários e armazenamento de 
log centralizado para acesso conveniente e solução de problemas em nível de solução. O registro centralizado também permite rastrear interações individuais, auditar atividades
em seu contact center e armazenar o histórico de alarmes.
•	Sinalização de alarme flexível que aciona alarmes com base em eventos de manutenção de aplicativos, parâmetros de desempenho do sistema ou limites do Simple Network
Management Protocol (SNMP). Os alarmes são comunicados ao Genesys Administrator e podem ser gravados nos logs do sistema. Você pode configurar o sistema para converter 
alarmes em traps SNMP e enviá-los como e-mails para um endereço de Internet especificado. (O último habilita automaticamente as notificações de paging.) A camada de 
gerenciamento associa automaticamente os alarmes às soluções que eles afetam e armazena os alarmes como condições ativas no sistema até que sejam removidos por outro 
evento de manutenção ou eliminados pelo usuário.
•	Funções de gerenciamento de falhas, consistindo em detecção, isolamento e correção de falhas de aplicativos. Para configurações não redundantes, a camada de gerenciamento 
reinicia automaticamente os aplicativos que falham. Para configurações redundantes, essa camada suporta uma alternância para os aplicativos em espera e também reinici
a automaticamente os aplicativos que falham.
•	Monitoramento de host individual, incluindo registros de uso de CPU e memória e informações sobre processos e serviços em execução.
•	Suporte para ambientes distribuídos geograficamente.
•	Suporte para implantação remota de componentes Genesys, conforme executado no Genesys Administrator Extension.
•	Suporte SNMP para processamento de alarme e troca de dados SNMP com um sistema de gerenciamento de rede (NMS) compatível com SNMP. 
Como resultado, você pode integrar um NMS de terceiros com um sistema Genesys para servir como uma interface de usuário final para funções de controle e monitoramento 
e para funções de sinalização de alarme.

**Arquitetura da camada de gerenciamento**

![image](https://user-images.githubusercontent.com/52088444/155137244-e673e4b7-3115-4f32-8e4e-b27cb15e87e1.png)


**Na camada de gerenciamento**

•	O Agente de Controle Local (não mostrado no diagrama), localizado em cada host que a Camada de Gerenciamento controla e/ou monitora, é usado para iniciar e parar 
aplicativos, detectar falhas de aplicativos e comunicar funções de aplicativos no contexto de redundância.
•	O Message Server fornece processamento e armazenamento centralizados de todos os eventos de manutenção de aplicativos. Os eventos são armazenados como registros de 
log no banco de dados de log centralizado, onde ficam disponíveis para processamento centralizado adicional. O Message Server também verifica eventos de log configurados 
para acionar alarmes. Se detectar uma correspondência, ele envia o alarme para o Solution Control Server para processamento imediato.
•	O Solution Control Server é o centro de processamento da camada de gerenciamento. Ele usa Agentes de Controle Local para iniciar os componentes da solução na ordem 
correta, monitorar seu status e fornecer uma reinicialização ou alternância em caso de falha do aplicativo. O Solution Control Server também inclui quatro utilitários 
que fornecem a capacidade de parar T-Servers com facilidade, lidar com chamadas travadas no T-Server, enviar mensagens de log em nome de aplicativos e trocar informações
com o Solution Control Server. Esses utilitários podem ser instalados com ou sem o Solution Control Server.
•	O Genesys Administrator, um componente da camada de interação do usuário , exibe o status de todas as soluções Genesys instaladas e informações sobre cada alarme ativo, 
permite que o usuário inicie e interrompa soluções ou aplicativos únicos (incluindo aplicativos de terceiros) e permite seleção e visualização avançadas de registros de 
manutenção.
•	O banco de dados de registro centralizado (também chamado de banco de dados de registro) armazena todos os registros de registro de aplicativos, incluindo registros 
relacionados à interação, registros de histórico de alarmes e registros de auditoria.
•	O SNMP Master Agent (um componente opcional não mostrado no diagrama) fornece uma interface entre a camada de gerenciamento e um NMS compatível com SNMP. Ele é necessário
para dar suporte a qualquer sistema de monitoramento de rede habilitado para SNMP e à tecnologia MOM (Microsoft Operational Manager).


## User Interaction Layer:

A camada de interação do usuário (User Interaction Layer )fornece uma interface de usuário abrangente para configurar, monitorar e controlar o ambiente de gerenciamento.

**A camada de interação do usuário fornece funcionalidades e interfaces centralizadas baseadas na web para o seguinte:**
•	Implantação de componentes Genesys em qualquer computador na rede usando o Genesys Deployment Agent (um componente da camada de gerenciamento). A partir da versão 8.5, 
essa funcionalidade faz parte do Genesys Administrator Extension.
•	Configuração, monitoramento e controle de aplicativos e soluções.
Atualmente, o Genesys Administrator e sua extensão é o único componente na camada User Interaction.

**Arquitetura da camada de interação do usuário**
![image](https://user-images.githubusercontent.com/52088444/155137694-6300d1c2-25c8-4dfd-bccb-9e4d0af35027.png)

**Na camada de interação do usuário:**

•	O Genesys Administrator baseado em navegador inclui uma interface de usuário abrangente para configurar, monitorar e controlar o ambiente de gerenciamento.
•	O servidor de gerenciamento da Web:
•	Comunica-se com o Servidor de Configuração (um componente da Camada de Configuração) para trocar informações de configuração.
•	Comunica-se com o Solution Control Server (um componente da camada de gerenciamento) para trocar informações de status, operações e controle.
•	Lê os logs do banco de dados de logs centralizado (um componente da camada de gerenciamento).
•	Fornece serviços da Web para o Genesys Administrator baseado em navegador.
•	Dependendo das soluções implantadas no sistema, o Web Management Server também pode se comunicar com outros servidores back-end para recuperar informações específicas 
da solução.
Media Layer: A camada de mídia (Media Layer ) permite que as soluções da Genesys se comuniquem através da mídia, incluindo sistemas de telefonia tradicionais, Voz sobre 
IP (VOIP), e-mail e Web. Essa camada também fornece o mecanismo para distribuir dados de negócios relacionados à interação dentro e entre as soluções.

**A camada de mídia fornece:**

•	Interfaces para meios de comunicação.
•	Distribuição de dados de negócios relacionados à interação dentro e entre soluções.

**Arquitetura de camada de mídia**
![image](https://user-images.githubusercontent.com/52088444/155137832-072d680b-1660-4265-b805-b725fd303187.png)

**Na camada de mídia:**

•	O Interaction Server fornece uma interface com mídia da Internet, como e-mail e comunicações na web. T-Server fornece uma interface com sistemas de telefonia tradicionais.
•	Os T-Servers fornecem uma interface com os sistemas de telefonia tradicionais.
•	T-Servers for IP Solutions fornecem uma interface com sistemas de telefonia VoIP.

Todos esses servidores comunicam solicitações de processamento de interação das soluções Genesys para os dispositivos de mídia e distribuem eventos de processamento de interação
na direção oposta. Eles também mantêm o estado atual de cada interação e todos os dados de negócios coletados sobre cada interação durante os estágios de processamento.
Esses servidores distribuem dados anexados a todos os aplicativos que participam do processamento da interação. Eles também podem transferir esses dados entre vários sites
de processamento de interação.
Outro componente da camada de mídia, o Load Distribution Server (LDS), não mostrado no diagrama, aumenta a escalabilidade e a disponibilidade do sistema.

## Services Layer: 

A Camada de Serviços( Services Layer) gera os dados estatísticos usados para processamento de interação e relatórios do contact center.

**A Camada de Serviços fornece:**

•	Conversão de eventos relacionados ao gerenciamento de interações individuais em dados estatísticos, que são então usados para processamento de interações e 
relatórios do contact center.

**Arquitetura da camada de serviços**
![image](https://user-images.githubusercontent.com/52088444/155138059-c9bc6397-4897-4597-a2b5-9260b63d441e.png)

O Stat Server rastreia em tempo real os estados dos recursos de gerenciamento de interação e coleta estatísticas sobre o desempenho do contact center. 
As soluções da Genesys usam os dados estatísticos para gerenciar de forma mais inteligente as interações em tempo real. Por meio do Genesys Reporting, você pode usar 
os dados para gerar relatórios históricos e em tempo real do contact center.

