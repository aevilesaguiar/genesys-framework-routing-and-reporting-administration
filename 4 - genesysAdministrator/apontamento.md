
## REVISÃO: ARQUITETURA DO ADMINISTRADOR GENESYS

A imagem a seguir descreve o Genesys Administrator - uma interface de usuário associada à User Interaction Layer -. Genesys Administrator é composto por:

- Navegador de Internet( web server)
- Administrador Genesys

Genesys Administrator(GA) é uma interface de usuário que é acessada usando um navegador da web. O GA está conectado ao Servidor de Configuração que lhe dá acesso às informações da Camada de Configuração. O GA autentica logins, lê e faz alterações nos objetos de configuração. O GA também possui conexões com o Solution Control Server. Isso dá à interface a capacidade de ver informações de status sobre aplicativos, iniciar e parar aplicativos, ver se algum alarme foi acionado e limpar alarmes acionados. O GA também se conecta ao banco de dados da Camada de Gerenciamento(Managment Layer ) para visualizar mensagens de eventos de log dentro da interface.

![image](https://user-images.githubusercontent.com/52088444/152349874-8d932442-3249-4c3e-9c6f-cf4b3a854cc7.png)

## servidor web (WEB SERVER)

O  Genesys Administrador é implantado em um servidor da Web e pode ser acessado usando um navegador da Web.

![image](https://user-images.githubusercontent.com/52088444/152350265-c5f931c1-922c-48ee-8b67-e48b42a4eab0.png)
![image](https://user-images.githubusercontent.com/52088444/152350322-1651b524-3fce-4fe8-b10b-ae906cbb96c3.png)


## NAVEGADORES DA WEB(WEB BROWSERS)

O administrador Genesys é um aplicativo da web que é acessado usando um navegador da web. Você abre um navegador da web, como o Firefox, digita a URL (endereço da web) e acessa o login para a interface Genesys Administrator, os navegadores suportados são:
![image](https://user-images.githubusercontent.com/52088444/152350825-27b82069-2ef0-4414-ac22-00e8d38f9bcb.png)

## HABILITANDO A IMPLANTAÇÃO COM O ADMINISTRADOR GENESYS(ENABLING DEPLOYMENT WITH GENESYS ADMINISTRATOR)


Se você for usar o Genesys Administrator para implantar aplicativos e soluções Genesys em qualquer host em sua rede, deverá instalar e executar a versão mais recente do LCA em cada host de destino. Isso instalará e iniciará o agente de implantação remota (referido como Genesys Deployment Agent) (GDA), que é usado pelo Genesys Administrator para realizar a implantação nesse host.

O Genesys Deployment Agent faz parte do pacote de instalação do Local Controle Agent(LCA) e é instalado automaticamente com o LCA. O Genesys Deployment Agent fornece a interface para copiar os pacotes e modelos de instalação necessários para seu host e, em seguida, instalá-los e configurá-los em um nível básico.

O Genesys Administrator pode implantar um aplicativo ou solução em um local local ou remoto, desde que o local atenda a ambos os critérios a seguir:

- O local de destino (The target location)deve ter um objeto Host configurado no Banco de Dados de Configuração.(Configuration database)

- A versão mais recente do LCA deve ser instalada nesse computador de destino. O Genesys Deployment Agent , instalado com o LCA , deve ser iniciado nesse local.


## CONEXÕES DO ADMINISTRADOR GENESYS( GENESYS ADMINISTRATOR CONNECTIONS)

Muitas funções do Administrador são fornecidas por meio de outros componentes da Genesys. Para habilitar essas funções, o Genesys Administrator precisa das seguintes conexões:

**Configuration Server(Servidor de Configuração)**

- Fornece acesso aos dados de configuração.
- Essas conexões são habilitadas automaticamente após a instalação do administrador

**Log DB Server Acess Point**

- Fornece acesso às mensagens de log
- Esta conexão precisa ser configurada após a instalação do administrador. Pode ser configurado com Genesys Administrator.

**Servidor de controle de solução**

- Fornece as informações de status do aplicativo e a funcionalidade de iniciar/parar
- Esta conexão precisa ser configurada após a instalação do Administrador. Pode ser configurado com Genesys Administrator.

Observação: o Genesys Administrator pode se conectar a vários aplicativos SCS e LodDAP e os usuários podem alternar entre eles conforme necessário sem precisar fazer logout.



## monitorando o status dos componentes do framework(monitoring status of framework components)

O Genesys Administrator pode começar a monitorar o status dos componentes da estrutura implantados dos componentes da camada de gerenciamento que estão configurados.

O Genesys Administrator pode ser implantado logo após a implantação do Configuration Layer.

Com o Genesys Administrator você pode instalar o Managment Layer(camada de gerenciamento), e Services Layer (camada de serviços).

Uma vez que o Managment Layer é implantado, você pode configurar conexões entre o Genesys Administrator e alguns componentes do Mangment Layer (será mostrado mais adiante) para iniciar o monitoramento do status dos componentes do Framework com o Gnesys Adminsitrator.


Nesta lição, mostraremos apenas como o Genesys Administrator é implantado. Nas lições a seguir, mostraremos como implantar componentes do Framework com o Genesys Administrator.

##  DEPLOYING GENESYS ADMINISTRATOR(IMPLEMENTANDO O ADMINISTRADOR DO GENESYS)


Para implantar o Genesys Adminsitrator, você deve executar três etapas:

![image](https://user-images.githubusercontent.com/52088444/152358759-f3e60704-04ad-4fe1-af79-29cec5dba53a.png)
![image](https://user-images.githubusercontent.com/52088444/152358836-4ffe04f1-551a-4630-9eb4-3e6ba4b5b8f7.png)
![image](https://user-images.githubusercontent.com/52088444/152358921-313a7960-65fa-4090-9b3a-1b1be0e6ca18.png)

## MASTER ACCOUNT 

Quando o banco de dados de configuração é inicializado, uma conta mestre com nome de usuário = padrão e uma senha = senha é criada.

O usuário padrão não é atribuído a uma função. Todos os outros usuários devem ser atribuídos a uma função para acessar aplicativos como Genesys Administrator e Interaction Wokspace.

![image](https://user-images.githubusercontent.com/52088444/152359537-289054ab-6e73-473c-96c1-760150ebbab7.png)

A conta mestra sempre existe no sistema e por design é sempre garantida Permissões de controle total para todos os objetos no Configuration DataBase e o acesso do usuário padrão a todos os objetos na configuração não podem ser excluídos ou modificados. Essa conta é usada ao efetuar login na camada de configuração pela primeira vez.

Esta conta Master é a mesma por padrão em todas as implementações Genesys, portanto, por motivos óbvios **é aconselhável alterar a senha associada a esta conta**. Dada a importância desta conta, tome cuidado especial para nunca perder a senha, pois ela não pode ser recuperada.

A conta de usuário padrão não está relacionada a funções e, portanto, não precisa ser atribuída a uma função,

A conta de usuário padrão não está relacionada a Grupos de Acesso e, portanto, não aparece como membro de nenhum Grupo de Acesso.

Esta conta mestra será usada para o primeiro login no Genesys Administartor.

