# Questionário Sistemas Embarcados I

## 1. Explique brevemente o que é compilação cruzada (***cross-compiling***) e para que ela serve.
R: A compilação cruzada, ou cross-compiling, é um processo no qual o código-fonte de um programa é compilado em um ambiente de desenvolvimento diferente daquele em que será executado. Em vez de compilar o código diretamente para a arquitetura e sistema operacional em que o desenvolvedor está trabalhando, o compilador é configurado para gerar código para uma plataforma de destino específica.

## 2. O que é um código de inicialização ou ***startup*** e qual sua finalidade?
R: Um código de inicialização, ou startup, é um conjunto de instruções executadas quando um sistema é inicializado ou um programa é lançado. Sua finalidade é preparar o ambiente de execução para a operação do software, configurando recursos essenciais, como memória, registradores, pilha, variáveis de ambiente e outros componentes do sistema. Em sistemas embarcados, o código de inicialização também pode ser responsável por configurar dispositivos de hardware e estabelecer comunicação com outros sistemas. 

## 3. Sobre o utilitário **make** e o arquivo **Makefile responda**:

#### (a) Explique com suas palavras o que é e para que serve o **Makefile**.
R: O Makefile é um arquivo de configuração usado em conjunto com o utilitário make para automatizar o processo de compilação e construção de programas. Ele contém instruções sobre como o código-fonte deve ser compilado e vinculado para produzir o executável final, bem como quaisquer outras tarefas relacionadas à construção do software. O Makefile especifica as dependências entre os arquivos-fonte e os comandos necessários para executar as etapas de compilação, garantindo que apenas os arquivos modificados sejam recompilados, o que economiza tempo durante o desenvolvimento. Em suma, o Makefile fornece uma maneira organizada e eficiente de gerenciar o processo de construção de software em projetos complexos.

#### (b) Descreva brevemente o processo realizado pelo utilitário **make** para compilar um programa.
R: Leitura do Makefile: O make lê o arquivo Makefile no diretório do projeto para entender as regras e dependências definidas.

Determinação das dependências: O make analisa as dependências entre os arquivos-fonte e os arquivos de destino (como o executável final) especificados no Makefile.

Verificação de alterações: O make verifica quais arquivos foram modificados desde a última compilação, comparando as datas e horários de modificação dos arquivos fonte e dos arquivos de destino.

Execução dos comandos: Com base nas regras definidas no Makefile e nas dependências identificadas, o make executa os comandos necessários para compilar e vincular o código-fonte, gerando o executável final.

Conclusão: Após a execução dos comandos, o make conclui o processo de compilação e informa se a compilação foi bem-sucedida ou se houve algum erro.

O make executa esses passos de forma eficiente, recompilando apenas os arquivos que foram modificados e suas dependências, garantindo assim uma compilação rápida e eficaz do programa.

#### (c) Qual é a sintaxe utilizada para criar um novo **target**?
R: A sintaxe para criar um novo target em um arquivo Makefile para compilar um programa em C++ é bastante semelhante à sintaxe genérica, mas comuns comandos de compilação e vinculação específicos para C

target: dependencies
    command
Para compilar um programa em C++, normalmente usamos um compilador como g++. Portanto, um exemplo simples poderia ser:
meu_programa: arquivo1.cpp arquivo2.cpp
    g++ -o meu_programa arquivo1.cpp arquivo2.cpp
    
Neste exemplo:

meu_programa é o nome do alvo que queremos criar.
arquivo1.cpp e arquivo2.cpp são os arquivos de origem que o programa depende.
g++ -o meu_programa arquivo1.cpp arquivo2.cpp é o comando para compilar os arquivos de origem e gerar o executável meu_programa.
Certifique-se de ajustar o nome do alvo, das dependências e dos arquivos de origem conforme necessário para o seu projeto específico.

#### (d) Como são definidas as dependências de um **target**, para que elas são utilizadas?
R: As dependências de um target são definidas na linha do target no Makefile. Elas indicam quais arquivos ou outros targets devem estar atualizados antes que o target em questão possa ser construído. As dependências são usadas pelo utilitário make para determinar a ordem de construção e garantir que as regras sejam seguidas, recompilando apenas o que é necessário para criar o target desejado.

#### (e) O que são as regras do **Makefile**, qual a diferença entre regras implícitas e explícitas?
R: As regras do Makefile definem como um target é construído a partir de suas dependências. Elas consistem em três partes principais:

Alvo (Target): O nome do target que está sendo construído.
Dependências (Dependencies): Os arquivos ou outros targets que o target depende.
Comandos (Commands): As ações que o make deve executar para construir o target a partir das dependências.
Existem dois tipos principais de regras em um Makefile:

Regras Implícitas (Implicit Rules): São regras pré-definidas pelo make para construir determinados tipos de arquivos, como compiladores de linguagens como C, C++, etc. O make sabe como transformar um arquivo de origem em um arquivo objeto e, em seguida, como vincular esses objetos para criar um executável.

Regras Explícitas (Explicit Rules): São regras definidas pelo usuário no Makefile para construir targets específicos de forma personalizada. Essas regras são explicitamente declaradas pelo desenvolvedor e fornecem flexibilidade para definir como um target é construído, além de permitir ações mais complexas que não são cobertas pelas regras implícitas.

A principal diferença entre as duas está na origem da regra e na sua definição: as regras implícitas são pré-definidas pelo make, enquanto as regras explícitas são definidas pelo usuário no Makefile.

## 4. Sobre a arquitetura **ARM Cortex-M** responda:

### (a) Explique o conjunto de instruções ***Thumb*** e suas principais vantagens na arquitetura ARM. Como o conjunto de instruções ***Thumb*** opera em conjunto com o conjunto de instruções ARM?
R: O conjunto de instruções Thumb é uma versão compacta do conjunto de instruções ARM projetada para economizar espaço de código e melhorar o desempenho em sistemas com restrições de memória, como dispositivos embarcados. Neste conjunto de instruções, as instruções são codificadas em 16 bits, em comparação com as instruções de 32 bits do conjunto de instruções ARM.

As principais vantagens do conjunto de instruções Thumb incluem:

Economia de Espaço: As instruções de 16 bits ocupam menos espaço de memória do que as instruções de 32 bits, o que é crucial em dispositivos com recursos limitados de memória.

Melhor Eficiência de Cache: O código Thumb compacto pode resultar em uma melhor utilização do cache de instruções, reduzindo a pressão sobre a memória cache e melhorando o desempenho do sistema.

Menor Consumo de Energia: O processamento de instruções Thumb pode exigir menos energia do que o processamento de instruções ARM devido ao menor número de bits necessários para representar cada instrução.

O conjunto de instruções Thumb opera em conjunto com o conjunto de instruções ARM por meio de um mecanismo de comutação automática chamado de interworking. Isso permite que um processador ARM execute instruções tanto no modo Thumb quanto no modo ARM, alternando conforme necessário. Os pontos de comutação entre os modos Thumb e ARM são gerenciados automaticamente pelo processador, garantindo uma execução suave e eficiente do código em ambos os conjuntos de instruções. Essa flexibilidade permite aos desenvolvedores aproveitar os benefícios de cada conjunto de instruções conforme apropriado para diferentes partes do código, otimizando o desempenho e o consumo de recursos.

### (b) Explique as diferenças entre as arquiteturas ***ARM Load/Store*** e ***Register/Register***.
R: As arquiteturas ARM Load/Store e Register/Register referem-se a diferentes abordagens para acessar dados na arquitetura ARM.

ARM Load/Store:

Nesta arquitetura, operações de carga (load) e armazenamento (store) de dados na memória são realizadas exclusivamente através de instruções de acesso à memória, como LDR (load register) e STR (store register).
Para realizar operações aritméticas ou lógicas, os dados devem primeiro ser carregados nos registradores da CPU usando instruções de carga (load) e, em seguida, os resultados dessas operações são frequentemente armazenados na memória novamente usando instruções de armazenamento (store).
Essa abordagem é mais comum em arquiteturas onde o acesso direto à memória é menos eficiente em termos de tempo e recursos.
Register/Register:

Nesta abordagem, as operações de carga (load) e armazenamento (store) não são usadas para acessar a memória diretamente. Em vez disso, as operações aritméticas ou lógicas são realizadas diretamente entre registradores da CPU.
Os operandos para essas operações são diretamente fornecidos pelos registradores e os resultados também são armazenados nos registradores.
Essa abordagem é mais comum em arquiteturas onde o acesso direto aos registradores é rápido e eficiente, tornando desnecessário o uso frequente de operações de carga e armazenamento para manipulação de dados.
Em resumo, enquanto a arquitetura ARM Load/Store depende fortemente de operações de carga e armazenamento para acessar dados na memória, a arquitetura Register/Register enfatiza operações diretamente entre registradores, evitando a necessidade de acessos frequentes à memória. A escolha entre essas abordagens depende das características do hardware subjacente e das considerações de desempenho específicas do projeto.

### (c) Os processadores **ARM Cortex-M** oferecem diversos recursos que podem ser explorados por sistemas baseados em **RTOS** (***Real Time Operating Systems***). Por exemplo, a separação da execução do código em níveis de acesso e diferentes modos de operação. Explique detalhadamente como funciona os níveis de acesso de execução de código e os modos de operação nos processadores **ARM Cortex-M**.
R: Os processadores ARM Cortex-M possuem dois níveis de acesso de execução de código: privilegiado e não privilegiado, onde o privilegiado tem acesso completo ao hardware e a todas as instruções, enquanto o não privilegiado tem acesso restrito. Eles também oferecem vários modos de operação, como o modo principal de thread e modos de exceção, como SVC, IRQ, Abort e Undefined. Esses modos permitem ao sistema operacional gerenciar eventos específicos, como interrupções e exceções, garantindo uma execução segura e eficiente do código em sistemas baseados em RTOS.

### (d) Explique como os processadores ARM tratam as exceções e as interrupções. Quais são os diferentes tipos de exceção e como elas são priorizadas? Descreva a estratégia de **group priority** e **sub-priority** presente nesse processo.
R: Os processadores ARM Cortex-M tratam exceções e interrupções através de uma estrutura hierárquica de prioridades. Existem diferentes tipos de exceções, como exceções de interrupção, aborto de dados, aborto de pré-busca e instrução indefinida. Essas exceções são priorizadas em ordem hierárquica, com as exceções de interrupção geralmente tendo prioridade mais alta.

Para gerenciar as prioridades das exceções, os processadores ARM Cortex-M utilizam a estratégia de group priority e sub-priority. Nesse sistema:

Group Priority (prioridade de grupo): Define a prioridade global do grupo de exceções, que pode incluir várias fontes de exceção. Ou seja, cada grupo de exceções tem sua própria prioridade relativa.

Sub-Priority (subprioridade): Dentro de cada grupo de exceções, as exceções individuais têm uma subprioridade. Isso permite que exceções do mesmo grupo tenham prioridades diferentes.

O sistema de group priority e sub-priority permite um controle mais granular sobre a priorização de exceções, garantindo que as exceções mais críticas, como as de interrupção, sejam tratadas com prioridade máxima, enquanto outras exceções possam ser ajustadas dentro de seus grupos específicos de acordo com suas necessidades de prioridade relativa.

Em resumo, os processadores ARM Cortex-M tratam exceções e interrupções utilizando uma estrutura hierárquica de prioridades, com a estratégia de group priority e sub-priority para gerenciar eficientemente a priorização das exceções e garantir um comportamento previsível e responsivo do sistema em tempo real.

### (e) Qual a diferença entre os registradores **CPSR** (***Current Program Status Register***) e **SPSR** (***Saved Program Status Register***)?
R: Os registradores CPSR (Current Program Status Register) e SPSR (Saved Program Status Register) são ambos utilizados nos processadores ARM para armazenar informações sobre o estado atual ou anterior do processador, mas eles têm propósitos diferentes:

CPSR (Current Program Status Register):

O CPSR é utilizado para armazenar o estado atual do processador, incluindo informações como o modo de execução atual, o estado de interrupção, se o processador está em estado privilegiado ou não privilegiado, entre outros.
É um registrador de acesso de leitura e gravação que pode ser modificado durante a execução do programa para controlar o comportamento do processador.
SPSR (Saved Program Status Register):

O SPSR é utilizado para armazenar o estado do processador quando ocorre uma exceção, como uma interrupção ou uma chamada de sub-rotina, para que possa ser restaurado posteriormente.
Ele é usado para salvar o estado do CPSR antes que o processador entre em um modo de exceção, garantindo que o estado do processador antes da exceção seja preservado.
Cada modo de exceção tem seu próprio SPSR, permitindo que o estado do processador seja salvo e restaurado corretamente quando ocorre uma exceção.
Em resumo, o CPSR armazena o estado atual do processador durante a execução do programa, enquanto o SPSR é utilizado para salvar temporariamente o estado do processador durante uma exceção, garantindo que o estado anterior possa ser restaurado após o término da exceção.

### (f) Qual a finalidade do **LR** (***Link Register***)?
R: O LR (Link Register) é um registrador utilizado nos processadores ARM para armazenar o endereço de retorno de uma sub-rotina ou função. Ele é utilizado para "lembrar" o endereço de instrução para onde o programa deve retornar após a execução da sub-rotina. Em resumo, o LR é responsável por manter o endereço de retorno das chamadas de função, permitindo que o fluxo de execução do programa retorne ao ponto de chamada após a execução da sub-rotina.

### (g) Qual o propósito do Program Status Register (PSR) nos processadores ARM?
R: O Program Status Register (PSR) nos processadores ARM é um registrador que armazena informações sobre o estado atual do processador, incluindo o modo de execução, as flags de condição, informações sobre interrupções e privilégios do processador. Ele é utilizado para controlar o comportamento do processador durante a execução do programa, permitindo que o sistema operacional e o software de aplicação gerenciem eficientemente as exceções, interrupções e outras operações críticas. Em resumo, o PSR é essencial para controlar e monitorar o estado e o comportamento do processador ARM durante a execução do programa.

### (h) O que é a tabela de vetores de interrupção?
R: A tabela de vetores de interrupção é uma estrutura de dados em sistemas baseados em microcontroladores que mapeia as diferentes fontes de interrupção para os respectivos tratadores de interrupção. Cada entrada na tabela de vetores de interrupção corresponde a uma fonte de interrupção específica, como uma interrupção de hardware ou uma exceção de software, e contém o endereço da rotina de tratamento de interrupção correspondente. Quando uma interrupção é acionada, o processador consulta a tabela de vetores de interrupção para determinar qual tratador de interrupção deve ser executado para lidar com a interrupção. Essa tabela é crucial para o sistema operacional e o software de aplicação lidarem eficientemente com interrupções e exceções, garantindo uma resposta rápida e confiável a eventos críticos.

### (i) Qual a finalidade do NVIC (**Nested Vectored Interrupt Controller**) nos microcontroladores ARM e como ele pode ser utilizado em aplicações de tempo real?
R: 
O NVIC (Nested Vectored Interrupt Controller) é um componente crucial encontrado em microcontroladores ARM que lida com interrupções de maneira eficiente e organizada. Sua finalidade principal é gerenciar interrupções de forma "nested" (aninhada), o que significa que ele pode lidar com múltiplas interrupções simultaneamente e de forma hierárquica, priorizando-as conforme necessário. Isso é essencial em sistemas de tempo real, onde as interrupções podem ocorrer de forma imprevisível e precisam ser tratadas com rapidez e precisão.

Aqui estão algumas das principais funções e usos do NVIC em aplicações de tempo real:

Priorização de Interrupções: O NVIC permite que as interrupções sejam priorizadas com base em sua importância. Isso é crucial em sistemas de tempo real, onde algumas interrupções podem ter prioridade sobre outras.

Aninhamento de Interrupções: O NVIC suporta interrupções aninhadas, o que significa que uma interrupção de maior prioridade pode interromper o tratamento de uma interrupção de menor prioridade. Isso garante que as interrupções críticas sejam tratadas imediatamente, mesmo se ocorrerem durante o tratamento de outra interrupção.

Tratamento Eficiente de Interrupções: O NVIC fornece mecanismos eficientes para lidar com interrupções, minimizando o tempo de latência entre a ocorrência de uma interrupção e seu tratamento.

Configuração Flexível: O NVIC permite configurar diferentes fontes de interrupção e atribuir prioridades a elas de acordo com os requisitos específicos da aplicação.

### (j) Em modo de execução normal, o Cortex-M pode fazer uma chamada de função usando a instrução **BL**, que muda o **PC** para o endereço de destino e salva o ponto de execução atual no registador **LR**. Ao final da função, é possível recuperar esse contexto usando uma instrução **BX LR**, por exemplo, que atualiza o **PC** para o ponto anterior. No entanto, quando acontece uma interrupção, o **LR** é preenchido com um valor completamente  diferente,  chamado  de  **EXC_RETURN**.  Explique  o  funcionamento  desse  mecanismo  e especifique como o **Cortex-M** consegue fazer o retorno da interrupção. 
R: O mecanismo de retorno de interrupção no Cortex-M é gerenciado pelo valor especial chamado EXC_RETURN, que é armazenado no registrador LR (Link Register) quando uma exceção ocorre. O EXC_RETURN é um valor específico que indica ao processador como retornar da exceção e restaurar o contexto de execução anterior.

Quando ocorre uma interrupção, o processador automaticamente salva o valor atual do registrador LR no stack (pilha) como parte do processo de entrada na rotina de tratamento de interrupção. Esse valor do LR contém o EXC_RETURN, que é um código especial que informa ao processador como restaurar o contexto de execução após o término do tratamento da interrupção.

O valor do EXC_RETURN contém informações sobre o estado do processador antes da exceção, incluindo o modo de execução anterior (privilegiado ou não privilegiado), o tipo de exceção que ocorreu (interrupção, exceção de interrupção pendente, retorno de exceção, etc.), e outras informações relevantes para restaurar o contexto de execução corretamente.

Quando o tratamento da interrupção é concluído e o processador está pronto para retornar ao código interrompido, ele utiliza uma instrução BX LR (Branch and Exchange with Link Register), que direciona a execução para o endereço armazenado no registrador LR. Como o valor do LR contém o EXC_RETURN, o processador interpreta esse valor e restaura o contexto de execução conforme necessário, incluindo o modo de execução anterior e outras informações relevantes.

Em resumo, o Cortex-M utiliza o EXC_RETURN armazenado no registrador LR durante uma interrupção para garantir um retorno seguro e confiável ao contexto de execução anterior após o tratamento da interrupção. Isso permite que o processador mantenha um comportamento consistente e previsível em sistemas embarcados e de tempo real.

### (k) Qual  a  diferença  no  salvamento  de  contexto,  durante  a  chegada  de  uma  interrupção,  entre  os processadores Cortex-M3 e Cortex M4F (com ponto flutuante)? Descreva em termos de tempo e também de uso da pilha. Explique também o que é ***lazy stack*** e como ele é configurado. 
R: A principal diferença no salvamento de contexto durante a chegada de uma interrupção entre os processadores Cortex-M3 e Cortex-M4F está relacionada ao tratamento do contexto do ponto flutuante (FPU - Floating-Point Unit) e à presença do recurso "lazy stack".

Cortex-M3:

No Cortex-M3, que não possui unidade de ponto flutuante, o salvamento de contexto durante a chegada de uma interrupção geralmente envolve o salvamento dos registradores de propósito geral (GPRs) e possivelmente alguns registradores especiais, como o PC (Program Counter) e o LR (Link Register).
O uso da pilha é essencial para salvar e restaurar os registradores do contexto. Durante a entrada na rotina de tratamento de interrupção, os registradores são empilhados na pilha para preservar seu estado atual, e ao sair da rotina de interrupção, os registradores são desempilhados para restaurar o contexto anterior.
Cortex-M4F:

O Cortex-M4F possui uma unidade de ponto flutuante (FPU), o que adiciona uma complexidade extra ao salvamento de contexto durante as interrupções. Além dos GPRs, os registradores de ponto flutuante também precisam ser salvos e restaurados.
O uso da pilha também é essencial aqui, mas o salvamento e a restauração dos registradores do FPU geralmente consomem mais tempo devido ao tamanho maior dos registradores de ponto flutuante em comparação com os GPRs.
Lazy Stack:

O conceito de "lazy stack" é uma técnica de otimização que adia o salvamento de alguns registradores na pilha até que seja realmente necessário. Em contextos de interrupção, onde o tempo de resposta é crítico, isso pode ser vantajoso para reduzir o tempo de latência.
O "lazy stack" pode ser configurado através do controle de configuração do NVIC (Nested Vectored Interrupt Controller). Ele permite configurar quais registradores devem ser salvos imediatamente durante uma interrupção e quais podem ser salvos de forma adiada, dependendo das necessidades específicas da aplicação e das interrupções envolvidas.

## Referências

### Básicas

[1] [STM32F411xC Datasheet](https://www.st.com/resource/en/datasheet/stm32f411ce.pdf)

[2] [RM0383 Reference Manual](https://www.st.com/resource/en/reference_manual/rm0383-stm32f411xce-advanced-armbased-32bit-mcus-stmicroelectronics.pdf)

[3] [Using the GNU Compiler Collection (GCC)](https://gcc.gnu.org/onlinedocs/gcc/index.html)

[4] [GNU Make](https://www.gnu.org/software/make/manual/html_node/index.html)

### Vídeos Microsoft Teams

[5] [05 - Introdução à arquitetura de computadores](https://web.microsoftstream.com/embed/channel/f6b3a0de-e6f3-4652-b2d5-f1164032498a?app=microsoftteams&sort=undefined&l=pt-br#)

[6] [06 - Arquitetura Cortex-M Parte 1/2](https://web.microsoftstream.com/embed/channel/f6b3a0de-e6f3-4652-b2d5-f1164032498a?app=microsoftteams&sort=undefined&l=pt-br#)

[7] [07 - Arquitetura Cortex-M Parte 2/2](https://web.microsoftstream.com/embed/channel/f6b3a0de-e6f3-4652-b2d5-f1164032498a?app=microsoftteams&sort=undefined&l=pt-br#)

[8] [08 - Microcontroladores STM32](https://web.microsoftstream.com/embed/channel/f6b3a0de-e6f3-4652-b2d5-f1164032498a?app=microsoftteams&sort=undefined&l=pt-br#)

[9] [10 - Introdução à arquitetura de computadores](https://web.microsoftstream.com/embed/channel/f6b3a0de-e6f3-4652-b2d5-f1164032498a?app=microsoftteams&sort=undefined&l=pt-br#)

### Material Suplementar

[5] [A General Overview of What Happens Before main()](https://embeddedartistry.com/blog/2019/04/08/a-general-overview-of-what-happens-before-main/)
 
[6] [Bare metal embedded lecture-1: Build process](https://youtu.be/qWqlkCLmZoE?si=mn5yDnJYudQ1PpZH)
 
[7] [Bare metal embedded lecture-2: Makefile and analyzing relocatable obj file](https://youtu.be/Bsq6P1B8JqI?si=yuNLPj3JQ-2IT1yo)
 
[8] [Bare metal embedded lecture-3: Writing MCU startup file from scratch](https://youtu.be/2Hm8eEHsgls?si=c27MpZ47ApiMSwHR)
 
[9] [Lecture 15: Booting Process](https://youtu.be/3brOzLJmeek?si=MsHRUEJP8zofjwJQ)
