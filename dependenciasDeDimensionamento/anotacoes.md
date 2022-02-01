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
