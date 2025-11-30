Simulando um Ataque de Brute Force de Senhas com Medusa e Kali Linux

Configuração do Ambiente

1.1. Topologia da Rede
O ambiente de teste foi configurado em modo isolado para simulação ética de ataques.

Software de Virtualização: VirtualBox.
Modo de Rede: Rede Interna (Host-Only).

Cenário de Ataque: Força Bruta em FTP com Medusa

2.1. Objetivo do Teste
Obter acesso não autorizado ao serviço FTP (porta 21) do Metasploitable 2.0 através da ferramenta Medusa, testando combinações de usuários e senhas.

2.2. Wordlists Utilizadas
Para simular um ataque de dicionário, foram criadas wordlists simples.

Wordlist de Usuários (users.txt ):
	user 
  msfadmin 
  admin 
  root

Wordlist de Senhas (pass.txt):
  123456 
  msfadmin 
  admin 
  root

2.3. Comandos Utilizados
A ferramenta Medusa foi utilizada com os seguintes parâmetros:

-H = Host: Endereço IP do alvo.

-U = User File: Caminho para a wordlist de usuários.

-P = Password File: Caminho para a wordlist de senhas.

-M = Module: Módulo de serviço a ser testado (ftp).
	
Comando Executado: 
medusa -H 192.168.56.102 -U user.txt -P pass.txt -M ftp -t 6

Obs: o “-t 6” significa que a saída será executada em 6 threads simultâneos


2.4. Resultado e Validação de Acesso
 Status: Sucedido.
 Credenciais Comprometidas: O ataque identificou as credenciais msfadmin:msfadmin como válidas.
 Validação Manual (Cliente FTP): O acesso foi validado conectando-se manualmente ao servidor FTP utilizando as credenciais encontradas.


Recomendações de Mitigação
Para prevenir ataques de força bruta e mitigar a vulnerabilidade explorada, as seguintes ações são recomendadas:

1. Desativar/Remover Contas Padrão:
Remover ou desabilitar imediatamente quaisquer contas padrão ou com credenciais de fábrica (ex: msfadmin).

2. Políticas de Senha Fortes:
Implementar uma política que exija senhas longas e complexas (combinação de letras maiúsculas/minúsculas, números e caracteres especiais).

3. Limitação de Taxa e Bloqueio de IP:
Configurar o firewall do servidor (ou o próprio serviço FTP, se suportado) para bloquear temporariamente o endereço IP de origem após um número predefinido de tentativas de login falhas (ex: 5 tentativas em 5 minutos).

4. Logs e Monitoramento:
Monitorar ativamente os logs de acesso ao FTP para detectar padrões de tentativas de login repetidas e malsucedidas, o que pode indicar um ataque em andamento.

5. Uso de SSH/SFTP (Preferencial):
Substituir o FTP (que transmite credenciais em texto simples) pelo SFTP (FTP sobre SSH) para criptografar o tráfego de dados e credenciais, protegendo contra interceptação (sniffing) e adicionando uma camada extra de segurança.

6. Listagem de Sites/Sistemas e E-mail Temporário
Para usuários simples, em um local seguro (de preferência fora de dispositivos) armazene quais sites você costuma usar, caso for usar um site para testar um serviço utilize um e-mail temporário evitando posteriormente um vazamento de dados. Encerre contas em plataformas que não utiliza mais e esteja consciente a quais sites você deseja se conectar.

Recomendação de Segurança Ética (Aplicável a Mitigação 6)

A utilização de dados fictícios ou e-mails temporários para proteger sua privacidade é uma boa prática. No entanto, é crucial ter consciência da lei. No Brasil, crimes como Falsa Identidade (Art. 307) e Falsidade Ideológica (Art. 299) são configurados pela intenção (dolo) de obter vantagem indevida ou causar dano a terceiros.

Use e-mail temporário e dados genéricos/fictícios (ex: "Usuário Teste", "20/02/2000") apenas em plataformas com cadastros simples (como newsletters ou testes de serviço), onde o cadastro não gera obrigação legal, vantagem indevida ou prejuízo a terceiros.

É importante salientar que utilizar dados falsos ou de terceiros em cadastros oficiais, financeiros ou para obter benefícios (ex: bancos, empréstimos, sistemas governamentais) é ilegal e punível, pois a intenção passa a ser fraudulenta.

Apenas utilize dados fictícios somente em contextos de baixo valor e nunca use dados de terceiros reais.

	Take care!  			     @Serpentesis on Github



