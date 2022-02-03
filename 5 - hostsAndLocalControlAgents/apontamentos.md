## Hosts

Um host é o servidor ou computador onde o aplicativo Genesys está instalado. Associado a esse computador ou servidor na Camada de Configuração está um objeto Host que contém todas as informações sobre a configuração da máquina Host.

Não existe uma instalação real chamada Host, no entanto, existem instalações que estão associadas e procuram informações no Host . Estes são o Local Control Agent e o Genesys Deployment Agent.

No exemplo, há cinco máquinas host diferentes sendo usadas. Isso significa que cada máquina Host tem um:


- Instalação do aplicativo Genesys que o torna um Host.
- Objeto Host associado na Camada de Configuração(Configuration Layer)
- instalação do Agente de Controle Local(Local Control Agent).
- Instalação do Genesys Deployment Agent.
![image](https://user-images.githubusercontent.com/52088444/152405302-f26151df-e595-4697-89d0-1a705a0d0396.png)

A configuração do host multiple será abordada posteriormente em uma lição posterior deste curso

## Host object

Uma vez que o Host tenha o aplicativo Genesys instalado, juntamente com LCA e GDA, o Host Object precisa ser configurado. Para configurar as propriedades gerais de um Host Object no Genesys Administrator, vá para
Provisioning>Environment> Hosts.

![image](https://user-images.githubusercontent.com/52088444/152406635-0d035cfb-a773-4e7b-a230-bf806f1ee878.png)

Quando outros aplicativos Genesys são instalados, o Host Object é verificado e procura outros objetos de aplicativo associados a este Host.

Nas propriedades de um objeto de aplicação existe uma propriedade para Host. Ao configurar novos aplicativos Genesys, você navega e seleciona o objeto Host, como o Configuration Server faz no exemplo acima

## SEGURANÇA DA CAMADA DE TRANSPORTE (TLS) - OPCIONAL

A Genesys suporta o uso opcional do protocolo Transport Layer Security (TLS) para proteger a troca de dados entre seus componentes. Todos os componentes Genesys são configurados no Genesys Adminsitrator. Para possibilitar a troca segura de dados entre os componentes, deve-se configurar parâmetros adicionais nos objetos Host e nos objetos Application que representam esses componentes.

Para usar a funcionalidade Genesys TLS, você deve concluir as seguintes etapas

![image](https://user-images.githubusercontent.com/52088444/152410994-07b9f7e3-8603-4cc6-b94b-7d231b32e424.png)
![image](https://user-images.githubusercontent.com/52088444/152411070-1c26e89c-7091-4b6f-94aa-fa5d45888b57.png)
![image](https://user-images.githubusercontent.com/52088444/152411134-6f498cfc-31a5-4c03-aae6-ac1a2ec2e207.png)

A Genesys recomenda que, a menos que você tenha motivos convincentes para ter qualquer um de seus aplicativos e/ou portas protegidos por seu próprio certificado individual, você mantenha a atribuição do certificado no nível do host e, em seguida, use os certificados de hosts para fornecer troca de dados segura para todos os aplicativos residentes em seus hosts.

Nota: você pode gerar o certificado e as chaves privadas correspondentes usando ferramentas padrão de infraestrutura de chave pública (PKI), como OpenSSL e serviços de certificados do Windows.

Consulte o Genesys 8.x Security Deployment Guide para obter informações detalhadas sobre pré-requisitos de ambiente, geração e instalação de certificados e etapas de configuração.

## PORTAS DO AGENTE DE CONTROLE LOCAL (LCA) AND GENESYS DEPLOYMENT (GDA)

Os dois aplicativos instalados no Host que são altamente dependentes do Host Object para obter informações são LCA e GDA. Os objetos host armazenam informações sobre esses aplicativos. Essas opções são lidas pela ferramenta de implantação.
A opção de porta do host é definida automaticamente durante a instalação do LCA. Ele só precisa ser alterado se a porta padrão do Deployment Agent foi modificada.

A porta do LCA é uma propriedade obrigatória do Objeto Host local. A porta padrão do Agente de Controle local é 4999, mas pode ser configurada para usar uma porta diferente.

Também associado ao Host Object está o Genesys Deployment Agent. A porta padrão do Deployment Agent é 5000, mas pode ser configurada para usar uma porta diferente. A porta padrão para GDA é encontrada na opção Host Object na seção[rdm]. Isso é visto na imagem abaixo.

Para configurar o LCA e o GDA , primeiro você precisa ter esses aplicativos instalados no Host. Durante a instalação, você executa a configuração do LCA e o LCA e o GDA são instalados no Host. LCA e GDA são instalados na mesma pasta, mas são dois executáveis ​​separados.

![image](https://user-images.githubusercontent.com/52088444/152416119-c0850df1-cb09-454b-ab6e-fc3dcf8a7f28.png)

## ARQUIVOS DE CONFIGURAÇÃO LCA E GDA: LOG (LCA AND GDA CONFIGURATION FILES: LOGGING) (PAGINA 100)


O log para LCA e GDA é um pouco diferente, pois não configuramos um objeto de aplicativo para LCA e GDA. No entanto, podemos alterar as configurações padrão para opções de log comuns para LCA e GDA.

Para fazer isso, edite o arquivo de configuração chamado lca.cfg para LCA e gda.cfg para GDA para especificar o nível de registro que você deseja ter em seu host.

Abra os arquivos com o Textpad. Nesses arquivos, especifique novos valores para as opções apropriadas. Os arquivos de configuração contêm apenas a seção de log. Você deve localizar esses arquivos no mesmo diretório que o arquivo executável LCA.
![image](https://user-images.githubusercontent.com/52088444/152417441-a6bf1dba-1056-4b58-b9a1-6421c67c9171.png)

No exemplo abaixo, o arquivo de configuração foi editado para usar a opção verbose para definir o nível de log que você deseja gerar - neste exemplo - para padrão.

![image](https://user-images.githubusercontent.com/52088444/152417784-c057dc22-9f06-485e-b8f9-4340ec9a76dc.png)

Quaisquer alterações feitas no arquivo de configuração LCA ou GDA entram em vigor na reinicialização do aplicativo.

