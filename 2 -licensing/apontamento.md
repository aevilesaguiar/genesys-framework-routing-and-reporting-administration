# Genesys License (Pagina 36)

**Componentes Genesys envolvidos**

![image](https://user-images.githubusercontent.com/52088444/152153963-6b454741-8f49-46d8-b2e3-aef21c006063.png)


## O arquivo de License

O formato de um arquivo de licença inclui um servidor, daemon e qualquer número de linhas de recurso(features).

Os parâmetros entre aspas "<>" abaixo indicam valores específicos para sua licença. A primeira linha do arquivo de licença é uma linha SERVER onde:

![image](https://user-images.githubusercontent.com/52088444/152154690-adbaf7c4-24a1-42a4-beda-b5b2ec7e0210.png)

O exemplo a seguir mostra o tipo de informação no arquivo de licença:

![image](https://user-images.githubusercontent.com/52088444/152154888-e964c2f4-da64-462d-904b-09378192d6cb.png)


O arquivo de licença do genesys contém itens vendáveis. Essas linhas FEATURE começam com números de produto hexadecimais de 12 dígitos que são linhas de itens vendáveis. Essas linhas de recursos não são verificadas pelo gerenciador de licenças.

![image](https://user-images.githubusercontent.com/52088444/152155451-d99cb11d-4d3f-4ef9-aacb-c489f63c6acf.png)

## Modificando o arquivo de licença

Os seguintes itens podem ser modificados sem invalidar a licença:
![image](https://user-images.githubusercontent.com/52088444/152155755-f1809744-25df-4116-bcff-6fe9f9d95794.png)


Nota: na linha DAEMON, não altere o nome do daemon em si. Você pode alterar o caminho para o daemon. Normalmente, '/path_here' é excluído, então a linha se parece com:

![image](https://user-images.githubusercontent.com/52088444/152156145-84a8027c-f404-4a7d-b7f1-ae11cd343966.png)

## Exemplos de licenças

há vários produtos Genesys que são licenciados. Uma licença pode não ser necessária para que o aplicativo seja iniciado, mas é necessária para determinadas funcionalidades. Nesta aula, veremos alguns desses exemplos:

![image](https://user-images.githubusercontent.com/52088444/152156667-587a003b-35c8-4c9f-b5db-1a291986bd14.png)



A Camada de Configuração(configuration layer) tem alguns recursos que exigem licenciamento. O Servidor de Configurações pode ser implantado em:
![image](https://user-images.githubusercontent.com/52088444/152156980-eb4b09f4-16d9-41ff-9c63-09b94d5e8a59.png)

## Camada de configuração: Servidor de configuração(Configuration Layer : Configuration SERVER)

A partir da versão 8.5, o Configuration Server também usa o arquivo de licença para autenticar o direito de usar o software na inicialização de cada nova implantação do Genesys Framework. Os itens vendáveis ​​são exigidos pelo servidor de configuração para sua primeira inicialização com um banco de dados de configuração novo ou atualizado.

![image](https://user-images.githubusercontent.com/52088444/152157662-8dcbe5ef-a17d-43ab-8753-e1324afc088e.png)


## MANAGMENT LAYER: SOLUTION CONTROLE SERVER(CAMADA DE GERENCIAMENTO: SERVIDOR DE CONTROLE DE SOLUÇÃO)

Habilite o SCS no modo distribuído

![image](https://user-images.githubusercontent.com/52088444/152158192-9448435e-ffc9-41c9-a991-5e07e9d95661.png)

## T-SERVER/SIP SERVER

A coisa mais importante a saber sobre o T-Server/SIP Server é que ele deve ser capaz de se conectar ao License Manager e obter pelo menos uma licença ou não será iniciado. Se o seu T-Server ou SIP Server não iniciar, esta é uma das primeiras coisas a verificar.

![image](https://user-images.githubusercontent.com/52088444/152158797-a2561f11-22de-41a6-bff5-5c10258c9475.png)

![image](https://user-images.githubusercontent.com/52088444/152158882-0840cb38-b043-427c-a4e2-73c724786ed3.png)

![image](https://user-images.githubusercontent.com/52088444/152159013-86ed905e-898c-46b4-9c63-f263305265fd.png)

![image](https://user-images.githubusercontent.com/52088444/152159091-24a44291-7430-44a9-be35-172d1ca9391b.png)

![image](https://user-images.githubusercontent.com/52088444/152159252-91530634-500a-4788-87fa-da3f0976cc2f.png)

![image](https://user-images.githubusercontent.com/52088444/152159741-7d12b20e-b55b-456d-812f-c6e931ae6c5d.png)
pagina 57