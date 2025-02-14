&emsp;&emsp;Esse documento apresenta o levantamento de requisitos para um jogo de forca online, conforme solicitado na atividade ponderada "Git na Prática: Controlando as Versões de seu Código".<br/>
&emsp;&emsp;A seguir estão dispostos os requisitos funcionais desse sistema e os seus testes de validação.<br/>
&emsp;&emsp;Caso necessário, as regras do jogo da forca, que foram consideradas para a construção desse documento podem ser acessadas <a href="https://pt.wikipedia.org/wiki/Jogo_da_forca">aqui</a>. 

## Requisitos Funcionais (RFs) 
&emsp;&emsp;Os requisitos funcionais do sistema estão dispostos a seguir:

<div align="center">
<sup>Quadro 1 - Requisitos Funcionais</sup>

| **ID**   | **Descrição**  | **Pré-condição**  | **Procedimento**  | **Resultado esperado**  | **Pós-condição**  |
|---------|-------------|-----------------|----------------|----------------------|----------------|
| **RF01** | O jogador deve ser capaz de iniciar uma nova partida individual. | O usuário deve estar na tela inicial. | Clicar no botão "Iniciar jogo" e, após isso, no botão "Modo Solo". | O sistema deve exibir a interface do jogo com uma palavra oculta, uma forca e o número de tentativas. | O usuário pode começar a jogar. |
| **RF02** | O jogador deve ser capaz de inserir uma letra por tentativa. | O jogo deve estar em andamento. | Digitar ou clicar em uma letra. | O sistema verifica a letra e atualiza a palavra oculta e tentativas restantes. | A interface reflete a tentativa realizada. |
| **RF03** | O sistema deve verificar automaticamente se o jogador venceu ou perdeu. | O jogo deve estar em andamento. | Jogar até acertar a palavra ou esgotar as tentativas. | (a) Caso o jogador acerte a palavra dentro do número de tentativas permitidas: O sistema exibe uma mensagem de vitória. (b) Caso o jogador não acerte todas as letras da palavra oculta dentro do número de tentativas permitidas: O sistema exibe uma mensagem de derrota. (c) Caso o jogador chute uma palavra de forma incorreta dentro do número de tentativas permitidas: O sistema exibe uma mensagem de derrota. | A partida é encerrada. |
| **RF04** | O jogador deve ser capaz de iniciar uma partida multiplayer com até 5 jogadores. | O usuário deve estar na tela inicial. | Clicar no botão "Iniciar Jogo" e, após isso, no botão "Criar uma partida multiplayer". | O jogador define uma palavra oculta ou solicita a geração de uma palavra aleatória e escolhe o nível de dificuldade; o sistema cria uma sala temporária e exibe um código para ingresso na partida. | A interface exibe o código de ingresso na tela. |
| **RF05** | O sistema deve permitir que jogadores ingressem em uma partida sem autenticação usando um código numérico temporário. | O anfitrião cria uma sala e compartilha o código. | O jogador insere o código na tela de entrada. | O sistema verifica o código e permite a entrada na partida. | O jogador pode participar da partida normalmente. |
| **RF06** | O sistema deve permitir a escolha de diferentes níveis de dificuldade com relação ao número de tentativas disponíveis. | O usuário está na tela de "Criar uma partida multiplayer". | Selecionar um nível de dificuldade. | O sistema ajusta a quantidade de tentativas e a complexidade das palavras. | O jogo inicia com os parâmetros selecionados. |
| **RF07** | O sistema deve permitir que os jogadores personalizem seus avatares. | O usuário está na tela de perfil. | Selecionar um avatar, dentre os personagens disponíveis. | O sistema deve atualizar o avatar do jogador. | O avatar aparece corretamente durante as partidas. |
| **RF08** | O jogador deve ser capaz de compartilhar o código de ingresso de uma partida para amigos participarem. | O sistema deve ter uma sala ativa no momento, criada por um jogador host. | O código deverá ser acompanhado de um componente para enviar o código em um clique via Whatsapp. | O amigo recebe uma mensagem com template padrão de convite e o link da partida. | O sistema adiciona o amigo à partida se ele aceitar. |
| **RF09** | O sistema deve distribuir a ordem de jogadas dos jogadores de forma ordenada e fixa em partidas multiplayer. | Uma partida multiplayer deve ser iniciada. | O jogador deve inserir uma letra ou uma palavra no campo de "palpite" ou "chute". | (a) Caso seja a vez do jogador: o sistema deve verificar a letra e atualizar o estado do jogo. (b) Caso não seja a vez do jogador: O sistema deve emitir um alerta de interface indicando ao jogador para esperar a sua vez. | Os jogadores jogam em uma sequência ordenada e fixa. |
| **RF10** | O sistema deve exibir um histórico de tentativas para cada jogador em partidas multiplayer. | A partida está em andamento. | O jogador deve visualizar a tela de jogo. | A interface deve mostrar as letras já tentadas por cada jogador. | O sistema evita a repetição inconsciente de palavras já sugeridas. |
| **RF11** | O sistema deve impedir que um jogador repita uma letra ou palavra já sugerida anteriormente. | A partida está em andamento. | O jogador deve inserir no campo de palpite uma letra ou palavra já palpitada anteriormente na partida. | A interface deve mostrar um alerta sobre a repetição e pedir um novo palpite. | O sistema continua a partida normalmente, mantendo a vez do jogador. |

<sub>Fonte: Material produzido pelo autor(2025).</sub>
</div>

## Requisitos Não Funcionais (RNFs)
&emsp;&emsp;Os requisitos não funcionais do sistema estão dispostos a seguir:

<div align="center">
<sup>Quadro 2 - Requisitos Não Funcionais</sup>

| **ID**   | **Descrição**  | **Pré-condição**  | **Procedimento**  | **Resultado esperado**  | **Pós-condição**  |
|---------|-------------|-----------------|----------------|----------------------|----------------|
| **RNF01** | O sistema deve carregar a tela inicial em no máximo 2 segundos. | O usuário acessa o jogo pela primeira vez. | Medir o tempo de carregamento da página. | O tempo registrado deve ser menor ou igual a 2 segundos. | O usuário pode interagir com a interface sem atrasos perceptíveis. |
| **RNF02** | O sistema deve ser responsivo e funcionar corretamente em dispositivos móveis e desktops. | O jogo é acessado em diferentes tamanhos de tela. | Verificar se o layout, os componentes e as cores são consistentes em resoluções variadas. | A interface se ajusta corretamente sem distorções de cores, quebra de layout ou omissão/distorção de componentes. | O jogo pode ser jogado de forma fluida em qualquer dispositivo. |
| **RNF03** | O sistema deve suportar até 100 partidas simultâneas sem degradação perceptível no desempenho, ou seja, sem perda de funcionalidade e sem demora consideravelmente superior de tempo de resposta. | O tempo de resposta do servidor com uma partida é registrado e, após isso, o servidor inicia múltiplas partidas ativas. | O tempo de resposta do sistema com 100 partidas concorrentes é registrado. | O sistema continua operando sem perda de funcionalidade e com o tempo de resposta igual ou de até 10% a mais em comparação com o tempo inicial registrado. | A experiência do usuário permanece estável. |
| **RNF04** | O sistema deve criptografar todas as comunicações entre cliente e servidor. | O usuário realiza ações no jogo. | Interceptar e inspecionar todas as requisições feitas ao servidor para verificar o uso de HTTPS e criptografia. | Todos as requisições interceptadas utilizam protocolo HTTPS e todos os dados trafegados estão criptografados. | As informações dos jogadores permanecem protegidas. |
| **RNF05** | O sistema deve manter a disponibilidade mínima de 99,5% ao longo do mês. | O sistema está implantado e operacional. | Monitorar uptime da aplicação com ferramentas de controle e monitoramento. | O tempo de inatividade da aplicação não ultrapassa 0,5% do tempo relativo a um mês comercial, cerca de 3 horas e 36 minutos. | O sistema permanece acessível para os usuários. |
| **RNF06** | O sistema deve garantir tempo de resposta inferior a 400ms para ações do jogador. | O jogador realiza uma ação no jogo. | Medir o tempo de resposta da ação. | O tempo registrado deve ser menor que 400ms. | O jogador percebe respostas rápidas e fluidas. |
| **RNF07** | O sistema deve seguir as diretrizes de acessibilidade (WCAG 2.1) para permitir o uso por pessoas com deficiência. | O jogo está acessível via navegadores compatíveis. | Realizar testes com leitores de tela e navegação por teclado. | O leitor de tela reconhece descrições de imagem e os textos presentes na interface e todos os componentes da interface podem ser acessados pelo teclado. | O jogo atende às normas e boas práticas de acessibilidade. |

<sub>Fonte: Material produzido pelo autor(2025).</sub>
</div>