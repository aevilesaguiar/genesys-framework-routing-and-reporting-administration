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
