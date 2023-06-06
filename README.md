# aaa

UNIVERSIDADE REGIONAL INTEGRADA DO ALTO URUGUAI E DAS MISSÕES
 CAMPUS DE ERECHIM 
DEPARTAMENTO DE ENGENHARIAS E CIÊNCIA DA COMPUTAÇÃO








GIANI PERTUZATTI, LEONARDO LUIS KLEIN, JOÃO PELICER





ATIVANDO VPN PPTP NO WINDOWS SERVER










ERECHIM - RS
2022





Sumário

Sumário	2
Introdução	3
Protocolo PPTP	4
Configuração do Protocolo PPTP	5
Configurando o Servidor PPTP	5
Placas de Rede	6
Atribuindo o servidor para um servidor VPN	7
Configurando usuário	16
Configurando o Cliente PPTP	19
Placa de rede	19
Conectando ao servidor	20
Conclusão	27
Referências	28


























Introdução
	
Neste trabalho, será apresentada uma documentação precisa de como ativar um protocolo de VPN em qualquer Windows Server. Para este exemplo, mostraremos como ativar um servidor PPTP, utilizando do Virtual Box para trabalharmos no Windows Server 2003 e assim simular o funcionamento do mesmo.


	

























Protocolo PPTP
	
	Segundo a fonte oficial da Microsoft, O PPTP(point-to-point tunneling protocol) é um dos protocolos VPN mais antigos utilizados hoje em dia, ele foi criado pela Microsoft com o objetivo de encapsular o PPP (Protocolo Ponto a Ponto).

Esse protocolo surgiu com o objetivo de promover a facilidade no acesso dos computadores remotos a uma rede privada, sendo assim, é uma linguagem que permite a comunicação entre os computadores.(Host green)























Configuração do Protocolo PPTP

	Vale ressaltar que para este passo a passo, utilizamos o Windows Server 2003, no entanto, segundo a Microsoft, fez um anúncio falando sobre o suporte estendido para o Windows Server 2003, que seria encerrado em 14 de julho de 2015. Isso significa que a Microsoft não oferece mais atualizações de segurança regulares, suporte técnico gratuito e opções de suporte estendido pagas para o sistema operacional.

	Portanto, não recomendamos utilizar a versão do Windows Server 2003 para escala comercial, caso queira fazer em um Windows Server mais recente, o passo a passo é extremamente igual ao Windows Server 2003.

Configurando o Servidor PPTP
	
	Nesta seção, será apresentado o passo a passo de configuração do servidor PPTP, o mesmo que está conectado na internet.

	A seguir, será apresentado a configuração das placas de rede no Virtual Box, para um Windows Server 2003.


Placas de Rede

	Como mencionamos anteriormente, necessitamos de duas placas de rede, uma que está conectada a internet e outra interna, para fazer a ligação com o cliente

	Para acessar as placas de rede no Virtualbox, você deve ir nas configurações da Máquina Virtual, e no painel à esquerda, deve encontrar a opção “Rede”.

Após, deve-se configurar duas placas de rede. Uma  conectado a NAT, e outra conectado em rede interna.

Figura: placa NAT. Os autores



Figura: placa de rede interna. Os autores
Atribuindo o servidor para um servidor VPN

	Agora, vamos atribuir o servidor que está sem uma função.

	Para adicionarmos uma função ao servidor, entramos na tela de gerenciamento do servidor, e clicamos em: Adicionar ou remover uma função.


	Figura: Adicionar Função. Os Autores


	Para o próximo passo, certifique-se que tem todos os recursos necessários para passar das etapas preliminares.


Figura: etapas preliminares. Os autores


	Para a próxima etapa, selecionamos a opção: Configuração Personalizada.

Figura: opção Configuração personalizada. Os Autores

	Agora, selecione a opção: Servidor de Acesso Remoto VPN, para abrir todo o painel de configurações para atribuir a função de Servidor VPN a este servidor.

Figura: opção Servidor de acesso remoto/VPN. Os autores

	Seguindo com o tutorial, avance a primeira janela. Quando chegar nas opções de configuração, marque a opção “Acesso a rede virtual privada (VPN) e NAT.

Figura: opção “Acesso a rede virtual privada (VPN) e NAT. Os autores


	Para esta etapa do tutorial, você deve selecionar a opção de placa de rede que está conectado à internet, que será a opção NAT.

Figura: opção NAT. Os autores

	Agora, selecione a opção da rede interna, que vai se conectar com o cliente para ter acesso a internet, no caso utilize a placa de rede interna que configuramos no VirtualBox.
 
Figura: opção Placa de rede interna. Os autores


No próximo passo, selecione a opção “De um intervalo de endereços específicos" para ter um controle melhor de endereços que vão utilizar esta VPN. 

Depois para a configuração do cliente, esse intervalo será importante.


Figura: intervalo de endereços. Os autores.


	Selecione novamente a rede interna para compartilhar a internet

Figura: opção Rede interna. Os autores


	Agora, selecione a opção “Ativar serviços básicos de nome e endereço” e avance. Assim você terá os endereços para o cliente se conectar.

Figura: endereços do VPN. Os autores


	Segundo, selecione a opção “Não, usar o Roteamento e acesso remoto para autenticar pedidos de conexão”.

Figura: Opção para usar o roteamento e acesso remoto para autenticação de pedidos de conexão. Os autores


	Pronto, seguindo esses passos, você terá atribuído a funcionalidade de VPN para este servidor.

Configurando usuário
	
	Agora que o servidor VPN está funcionando, devemos atribuir as permissões de acesso para o cliente. Para isso navegue no menu iniciar, após aponte para as ferramentas administrativas e selecione “Gerenciamento do computador”.

Figura: gerenciamento do computador. Os autores


	Na tela do Gerenciamento do computador, expanda a árvore de usuários e grupos locais, entre na pasta de usuários e dê dois cliques no perfil do administrador.

Figura: perfil do administrador. Os autores


	Dentro do perfil do administrador, acesse a guia de discagem, e permita o acesso remoto ao administrador, após isso clique em aplicar e em OK.

Figura: guia de discagem para o administrador. Os autores


	Pronto, agora está completo o passo a passo de como configurar o Servidor VPN, agora podemos fazer uma ligação com o cliente.


Configurando o Cliente PPTP

Nesta seção, será apresentado o passo a passo de configuração do cliente, que através do PPTP, será conectado à internet.

Placa de rede

	O cliente deverá ter uma placa de rede interna para conectar-se ao cliente.

Figura: placa de rede interna. Os autores


Conectando ao servidor
	Para conectar-se ao servidor, nossa placa de rede deve estar no intervalo atribuído antes, para o caso do tutorial é: de 10.1.62.1 até 10.1.62.200, totalizando 200 endereços

	Entrando nas configurações de rede, clicamos em arquivo, que está localizado no canto superior esquerdo, abrindo a aba arquivo, clique em nova conexão.

	Avançe a primeira tela, e após isso, clique na opção “Conectar-me a uma rede em meu local de trabalho”, para poder atribuir as funções VPN

Figura: opção Conectar-me a uma rede em meu local de trabalho. Os autores

	Avançando, clique na opção conexão VPN.

Figura: opção Conexão VPN. Os autores.

	Para o próximo passo, você deve dar um nome a empresa que você irá se conectar, pode ser qualquer nome, desde que você consiga achar e se conectar depois.

Figura: nome da empresa. Os autores


	Agora, você deve digitar o ip da placa de rede interna do servidor, para poder se conectar com a internet.

Figura: ip de conexão do servidor. Os autores


	Agora, selecione a opção “Ser usada por qualquer pessoa”.

Figura: opção Ser usada por qualquer pessoa. Os autores
	Pronto, agora você atribuiu uma conexão de rede VPN PPTP de um cliente para um servidor, agora basta fazer o login na rede com o usuário Administrador e sua respectiva senha.

Figura: login na rede. Os autores

Figura: internet conectada. Os autores

















Conclusão

	Em resumo, o trabalho realizado foi bem-sucedido ao conectar um servidor e um cliente utilizando o protocolo PPTP no Windows Server 2003. Essa conexão segura facilitou a transmissão de dados entre as partes envolvidas, proporcionando uma solução confiável para a comunicação através de redes públicas.

É importante notar, no entanto, que o Windows Server 2003 foi descontinuado pela Microsoft e não recebe mais suporte. Recomenda-se migrar para uma versão mais recente do sistema operacional para garantir a segurança e o suporte contínuos.

































Referências

O que é protocolo de Tunelamento Ponto a Ponto? - Hosts.green
<https://blog.hosts.green/pptp/>
Acesso em: 30 de Abril de 2023

Windows Server documentation
<https://learn.microsoft.com/en-us/windows-server/>
Acesso em: 28 de Abril de 2023

Como instalar e configurar um servidor PPTP
<https://learn.microsoft.com/pt-br/troubleshoot/windows-server/networking/install-configure-virtual-private-network-server>
Acesso em: 28 de Abril de 2023


