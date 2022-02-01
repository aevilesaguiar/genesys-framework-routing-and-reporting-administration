# Dimensionamento de Dependencias
![image](https://user-images.githubusercontent.com/52088444/151961586-40a84aeb-4ef5-4d55-a499-6e3b02c144f0.png)
         
**Numero e localização do Contact Center** Para uma implementação distribuida a principal consideração é o tamanho e confiabilidade da rede. O genesys pode ser distribuido entre sites.
**Configuração e capacidade da rede**  em testes, uma rede tcp/ip 100base-t mostrou-se mais do que adequada para lidar com um volume extraordinariamente alto de interações (mais de 100 chamadas por segundo) em uma implementação típica.
**Capacidade de Hardware w arquitetura** A estrutura da rede de dados pode ser interdependente de todas essas variáveis. Na prática geral, com CPU e capacidade de rede suficientes, uma arquitetura de sistema bem projetada será mais do que adequada até mesmo para os maiores volumes
**Numero e tipos de agentes** aumentando o numero de agentes geralmenta aumenta a velocidade com que a solução de roteamento pode lidar com as interações. Quanto mais agentes, o mais rapido a taxa de transferência, uma vez que o tempo de espera por um destino é reduzido os perfis dos agentes também podem afetar o tamanho, dependendo das considerações de design da estratégia.
**Padrões de interação e volume**  o número de interações recebidas são considerados juntamente com certos padrões: 
- Interações por segundo
- time de atendimento
- tamanho dos dados anexados
- porcentagem de todas as interações transferidas

## Diretriz de dimensionamento de banco de dados

O tamanho da configuração do banco de dados vai depender do tamanho do Contact Center, ou mais precisamente no número de entidades no contact center que você especifica como objetos de dados de configuração. Tipos de objetos configurados incluem pessoas, aplicativos, dns, logins de agentes.

Se a capacidade de armazenamento de dados for limitada, considere alocar 10KB de espaço para cada objeto no contact center como uma diretriz geral. 
caso contrário, alocar 300 MB acomoda um banco de dados de configuração para uma instalação corporativa típica. Ao contrário dos bancos de dados de registro e relatório, o banco de dados de configuração tem menos probabilidade de ultrapassar os limites de seu servidor DBMS.

- Orientações gerais(general guideline):
![image](https://user-images.githubusercontent.com/52088444/151965968-f01452ec-e5ec-4008-bb93-2519a1740371.png)

O banco de dados de log pode armazenar todos, exceto registros de log de nível de depuração, incluindo registros relacionados à interação, registros de histórico de alarmes e registros de auditoria. Como acontece com qualquer banco de dados histórico, o tamanho do banco de dados de log cresce com o tempo. Ao planejar sua instalação, tenha em mente que:

- Tamanho máximo do registro 1 KB
O dimensionamento do banco de dados depende de:
- aplicações (tipo e quantos)
- nivel de registro(log levels)
- quanto tempo os registros são mantidos(how long records kept)
- volume de chamadas(call volumes)

Para visualização online, permita mais 30%( for online viewing, allow another 30%)

**O tamanho máximo de registro permitido é 1 KB.

O tamanho do banco de dados dde log depende de:
- O numero e tipos de aplicação do sistema;
- o nível de log que você definiu para a saída de rede para cada aplicativo.
- o tempo necessário que os registros de log devem ser mantidos no banco de dados
- volume de chamadas(call volume)
- para uma visualização de log on-line eficiente, aloque espaço de banco de dados temporário em pelo menos 30% do tamanho do banco de dados de log esperado

Defina por quanto tempo os registros de log devem ser mantidos no banco de dados antes de se tornarem obsoletos. Use o assistente de manutenção do banco de dados de log para excluir registros obsoletos ou configurar a remoção de registros obsoletos usando os mecanismos do DBMS;

## dimensionamento e desempenho


Os recursos físicos disponíveis afetam o dimensionamento e o desempenho.Por recursos físicos, estamos nos referindo ao número e velocidade de processadores , quantidade de memória do computador, capacidade de armazenamento de dados , distribuição de aplicativos entre hosts e números e tipos de hosts.
os documentos de planejamento de implantação fornecem algumas diretrizes gerais para planejar os recursos do sistema. Lembre-se de que estas são diretrizes gerais e podem não ser diretamente aplicáveis ao seu ambiente.

![image](https://user-images.githubusercontent.com/52088444/151968824-74b554fb-19b5-497f-b5de-ca4c0c1ae57d.png)

## Requisitos de memória do componente

Para estimar a quantidade de memória do computador necessária para uma máquina servidora. identifique os componentes a serem instalados em cada servidor e, em seguida, as diretrizes de dimensionamento específicas listadas no guia de implantação para o componente envolvido.

Por exemplo, como todo o banco de dados de configuração é armazenado em cache na memória do servidor de configuração, a recomendação para o tamanho do banco de dados de configuração também é uma diretriz razoável para dimensionar os requisitos de memória de aplicação do servidor de verificação.


## Traffic requirements(Requisitos de trafego)

Para estimar a quantidade de tráfego de link entre os componentes, identifique os componentes a serem instalados em cada servidor e seu local de rede e, em seguida, consulte as diretrizes de dimensionamento específicas listadas no guia de dimensionamento de hardware do Genesys 8 para o componente envolvido. Ele fornece dados básicos sobre o tráfego de links entre vários componentes da estrutura.

## escolhendo um host

você pode usar essas informações para ajudá-lo a determinar a melhor localização do componente na rede.
Existem três considerações principais ao selecionar uma máquina para hospedar um servidor - notas a seguir:

- Minimize o tráfego de rede: colocar dois servidores no mesmo host reduz o tráfego de rede. Exemplo: T-server se comunica constantemente com Stat Server. Faz sentido localizar os dois servidores no mesmo host, para reduzir o tráfego de rede e acelerar a comunicação

- compartilhar recursos da CPU: Dois servidores no mesmo host devem compartilhar a CPU. Exemplo: T-Server e DB Server são intensivos em CPU. É melhor localizá-los em hosts separados.


- Use hosts multiprocessadores: um host multiprocessador é especialmente útil para servidores que geram processos filhos, como DB Server

**Notas**
- A adição ou modificação de objetos é sempre comunicada por meio de uma única transação. A exclusão de alguns objetos pode afetar outros objetos na configuração e levar a várias atualizações
- o uso de log de nível de interação e nível de rastreamento no modo de produção pode gerar alto tráfego e diminuir o desempenho do DBMS, servidor de banco de dados, servidores de mensagens, e o log de nível de interação e nível de rastreamento é geralmente destinado à depuração no local de nova interação - processamento de funções e cenários antes de serem colocados em modo de produção.
- O volume de tráfego pode aumentar para 'médio' em um contact center de médio a grande porte quando uma administração executa uma consulta SNMP extensa
