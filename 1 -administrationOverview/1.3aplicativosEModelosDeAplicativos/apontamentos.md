# Software : aplicativos e modelos de aplicativos


Os aplicativos Genesys são baseados em Modelos de Aplicativos. O modelo de aplicativo determina as propriedades associadas ao objeto de aplicativo e as propriedades que você definirá.
O modelo escolhido também determina quais guias e opções de aplicativos estarão disponíveis.
(Although ) Embora Embora o início de cada instalação seja um pouco diferente, a abordagem típica para configurar um aplicativo começa configurando o modelo de aplicativo e, em 
seguida, criando o objeto de aplicativo desejado com base no modelo. Você aprenderá isso em detalhes mais tarde na aula e praticará várias vezes.

No nível superior dos discos de instalação, há uma pasta de modelos que contém os arquivos de modelo para o software nesse disco. Os modelos são o ponto de partida para a configuração. 
A instalação é organizada por sistema operacional.

Existem três tipos de arquivos diferentes localizados na pasta de modelos:

- .tpl-contains os valores de opção padrão para aplicativos
- "apd- é gerado a partir do ".tpl" arquivo por uma ferramenta interna do genesys. Os arquivos .apd são equivalentes aos arquivos .tpl, mas os arquivos .apd estão em formato binário.
Este é o tipo que você usará para criar objetos de modelo de aplicativo.
-  .xml - também contém os valores de opção padrão, mas além disso contém mais informações, incluindo privilégios e parâmetros de inicialização.

Quando você está executando sua instalação, os objetos Modelo do aplicativo são criados importando o arquivo .apd desejado.

![image](https://user-images.githubusercontent.com/52088444/151976103-b1b53f06-3893-4a37-94c8-c0dcaa85f51b.png)


Ao fazer upload de um plug-in, o GAX usa o arquivo de modelo (.tpl) para criar um modelo de aplicativo e extrai as opções padrão para o plug-in.
O GAX armazena essas opções no banco de dados e as mescla com o objeto principal do aplicativo GAX na implantação. Durante essa mesclagem, apenas novas
opções são adicionadas - Os pares de valores-chave existentes não são substituídos.

## Os aplicativos são baseados no modelo de aplicativo

No genesys , um modelo de aplicativo para um tipo específico de aplicativo será usado várias vezes para criar aplicativos diferentes. Por exemplo, na imagem abaixo você pode ver.

Um modelo de aplicativo de servidor SIP é usado para criar cinco aplicativos de servidor SIP diferentes.

![image](https://user-images.githubusercontent.com/52088444/151977454-56f48348-e809-4ed2-a53e-eb65881ec302.png)


Cada um desses aplicativos pode ter suas próprias opções de configuração, onde está localizado, ser executado em seu próprio host, etc.
Mas tudo se baseia inicialmente nesse ponto de partida do modelo de aplicativo.

## Propriedades do aplicativo


Cada aplicativo no sistema GENESYS possui um objeto de aplicativo correspondente no banco de dados de configuração.
ao configurar o aplicativo, cada objeto do aplicativo tem sua própria folha de propriedades contendo as seguintes seções de dados de configuração.

**Informações gerais**
A seção geral é onde você define as propriedades gerais do objeto de aplicativo, normalmente seu nome e o nome do modelo no qual o aplicativo se baseia.

Insira o nome do aplicativo de acordo com seu plano de implementação. Por exemplo, Nome: Chicago SIP Server.
O modelo determina o tipo de objeto que este aplicativo representa. Para Exmape: TServer_SIPPremisse_8.1.101.34 representa um servidor SIP.

**Conexões**

Nesta seção, você criará conexões que este aplicativo possui com outros aplicativos. Pense nos diagramas de arquitetura da classe de operações. 
É aqui que você informa ao genesys sobre as conexões entre os aplicativos em sua arquitetura

![image](https://user-images.githubusercontent.com/52088444/151979908-8bc198eb-d322-4ddb-b50e-b26e533dfae3.png)

**Dependências**

Dependências exibe uma lista de todos os objetos que são dependentes desse objeto e de qual propriedade eles são dependentes.

**Portas**
A seção Portas exibe o número da porta atualmente em uso por todos os aplicativos que se comunicam com este objeto de aplicativo. No Genesys, 
é assim que os aplicativos se comunicam uns com os outros - usando portas numeradas semelhantes a como você usa um número de telefone para se comunicar com um amigo.

**Opções do aplicativo**
Você define as opções do aplicativo para personalizar o comportamento do aplicativo. As opções do aplicativo para cada tipo de aplicativo variam muito. As opções para um aplicativo T-Server, por exemplo . incluem parâmetros de comutação. As opções para um aplicativo State Server incluem definições de tipo estático. Algumas opções requerem valores válidos para operar, mas outras não.
As principais opções serão apresentadas nesta classe, mas há muito mais opções disponíveis no Genesys. Verifique a documentação da Genesys para obter os detalhes das opções individuais.
