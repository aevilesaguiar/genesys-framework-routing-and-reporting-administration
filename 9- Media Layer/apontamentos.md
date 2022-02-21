# Media Layer

Application Setup(Configuranso aplicação)

Mais de uma maneira de configurar o aplicativo com GAX:

- Configure application object >> Run setup.exe
ou

- Importar Pacote de Instalação (IP) >> INSTALL ip

## Solution Definition

Uma definição de solução é um arquivo XML que descreve o que está sendo implantado, como as implantações devem ser executadas, 
bem como quaisquer procedimentos necessários de pré e pós-instalação.

O Guia do Desenvolvedor GAX abrange a criação de arquivos de definição de solução.


## Media Layer Setup

![image](https://user-images.githubusercontent.com/52088444/154964643-b5051425-9e17-499b-bc90-84a8212d90ca.png)


A caixa cinza representa o Switch físico ou PBX. A rede pública (PSTN) com vários troncos se conecta ao PBX. O Switch físico ou PBX é o que corresponde ao Switch Office. Ao configurar o Switching Office, você informa que tipo de switch está usando.

As centrais de comutação são as centrais telefônicas reais que fornecem atendimento telefônico aos Contact Centers. Um escritório de comutação pode conter um ou mais objetos de comutação.
Cada objeto de switch é emparelhado com , e é controlado por um T-Server e representa uma coleção de recursos de telefonia (DN'S, Logins de Agentes)

É típico ter um escritório de comutação, um switch e um T-Server.

![image](https://user-images.githubusercontent.com/52088444/154966274-e7c8e172-01d1-4623-a8b1-9e416b073474.png)

- Central de comutação - As centrais de comutação são as centrais telefônicas reais que fornecem serviço telefônico aos centros de contato. Uma central de comutação pode conter um ou mais objetos de comutação (com DNs e Logins de Agente). Na maioria das configurações, um escritório de comutação contém um único switch

- Switch - Um switch é um objeto no banco de dados de configuração que representa um switch físico ou virtual. É uma coleção de recursos de tekephony (DN'S, agentes) dentro de um switch Office controlado por um T-Server;

- SIP Server/ T Server Aplication: Cada SIP Server/T-Server requer seu objeto de aplicação. Por exemplo, para instalar uma configuração multi-site com dois servidores SIP/T-Servers, você deve definir dois OBJETOS DE APLICAÇÃO de Servidor SIP/T-SERVER distintos 

-DN - DNs (números de diretório) representam dispositivos de comunicação onde as interações dos clientes (por exemplo, chamadas telefônicas) são tratadas. Tipos de DN comuns incluem Pontos de Roteamento (RP), Filas (Q) e Extensões (Ext). Na maioria dos casos, os DN'S no banco de dados de configurações devem corresponder exatamente à configuração do DNS no sistema de swithing.

- Login de agente - Logins de agente são códigos exclusivos definidos em uma central e atribuídos a agentes. Os logins do agente no banco de dados de configuração devem corresponder aos logins do agente no switch. Os logins de agente são usados para relacionar um usuário específico a uma sessão de trabalho específica. No Genesys , cada Login de Agente está associado a um agente ou pessoa específica . Apenas uma pessoa pode possuir o login a qualquer momento. No entanto, uma única pessoa pode possuir vários Logins de Agente. Por exemplo: se um agente logar em DNs em mais de um switch, esse agente precisará de um Agent Login em cada switch.

dentro do objeto Switch você pode criar:
- Agent Logins
- DN'S

Independentemente do tipo de T-SERVER/SIP Server, existem várias opções de aplicativos que precisam ser configuradas que são comuns. A seção T-Server contém as opções de configuração que são usadas para suportar os recursos principais comuns a todos os T- servidores.


