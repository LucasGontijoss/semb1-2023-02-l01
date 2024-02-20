# Questionário Sistemas Embarcados I

## 1. Explique brevemente o que é compilação cruzada (***cross-compiling***) e para que ela serve.
       É quando um programa é compilado em uma plataforma diferente da qual ele vai ser executado, é útil para desenvolver software para plataformas diferentes com recursos limitados daquela em que o desenvolvedor está trabalhando.

## 2. O que é um código de inicialização ou ***startup*** e qual sua finalidade?
       São instruções que são executadas quando o sistema se inicializa ou quando o programa é executado, a sua finalidade é preparar o ambiente para a execução do programa principal.

## 3. Sobre o utilitário **make** e o arquivo **Makefile responda**:

#### (a) Explique com suas palavras o que é e para que serve o **Makefile**.
      É um arquivo de texto em que tem instruções para automatizar o processo de compilação, e ele define as 'regras' para a compilação do programa.

#### (b) Descreva brevemente o processo realizado pelo utilitário **make** para compilar um programa.
       O processo é verificar as dependências de cada arquivo fonte e, se precisar, recompilar os arquivos que foram modificados.  

#### (c) Qual é a sintaxe utilizada para criar um novo **target**?
      targets: prerequisites
              	recipe  

#### (d) Como são definidas as dependências de um **target**, para que elas são utilizadas?
      É definido após o nome do target, representam os arquivos ou outros targets que o target atual depende para ser feito, o make usa essas dependencias para definir a ordem da compilação e recompilção do programa.
      
#### (e) O que são as regras do **Makefile**, qual a diferença entre regras implícitas e explícitas?
      São as instruções para como o programa deve ser compilado, as regras implicitas são as definidas pelo make e as explicitas são desenvolvidas pelo desenvolvedor. 

## 4. Sobre a arquitetura **ARM Cortex-M** responda:

### (a) Explique o conjunto de instruções ***Thumb*** e suas principais vantagens na arquitetura ARM. Como o conjunto de instruções ***Thumb*** opera em conjunto com o conjunto de instruções ARM?
    É uma versão compacta do conjunto de instruções ARM original, as vantagens dele é que ele utiliza apenas 16 bits para economizar espaço e melhorar a eficiência da memoria. O thumb opera em conjunto com o conjunto do ARM original, assim aproveitando a vantagem de ambos conjuntos de instruções.

### (b) Explique as diferenças entre as arquiteturas ***ARM Load/Store*** e ***Register/Register***.
    ARM Load/Store separa explicitamente as operações que acessa a memoria das operações do processamento, utilizando as intruções de load e sotre para acessar a memória. Já na Register/Register as operações para acessar a memoria são em conjunto das operações de processamento, que usa registradores de dados para acesso direto à memória.

### (c) Os processadores **ARM Cortex-M** oferecem diversos recursos que podem ser explorados por sistemas baseados em **RTOS** (***Real Time Operating Systems***). Por exemplo, a separação da execução do código em níveis de acesso e diferentes modos de operação. Explique detalhadamente como funciona os níveis de acesso de execução de código e os modos de operação nos processadores **ARM Cortex-M**.
    Para o acesso temos o Privileged Mode, em que concede ao software acesso total as instruções do processador, o software tera total controle sobre o sistema quando for executado neste modo, e o outro acesso é o Unprivileged Mode em que restringe o acesso do software a certas instruções, e tem acesso limitado a recursos do sistema e não pode executar certas instruções privilegiadas. Já os modos de operação é o Thread Mode onde é utilizado para execução normal de tarefas do usuário ou sistema, e as interrupções e exceções podem ser tratados de acordo com as configurações de prioridade, outro modo é o Handler Mode que é ativado quando uma interrupção ocorre priorizando o tratamento desses eventos em relação à execução normal do codigo, e tem o Privileged Mode em que o softwaree pode executar instruções privilegiadas e acessar recursos exclusivos do sistema.

### (d) Explique como os processadores ARM tratam as exceções e as interrupções. Quais são os diferentes tipos de exceção e como elas são priorizadas? Descreva a estratégia de **group priority** e **sub-priority** presente nesse processo.
    Ele trata as interrupções pelo sistema de priorização em  niveis de exceção e grupos de prioridade. Tem diversos tipos de interrupções, como reset, IRQ,FIQ e SVC e cada um tem sua propria prioridade. São criados grupos com as interrupções onde tem seus niveis de prioridade, e dentro de cada grupo são colocadas prioridades adicionais, onde esses grupos são o Group priority e as prioridades adicionais são as sub-priority.

### (e) Qual a diferença entre os registradores **CPSR** (***Current Program Status Register***) e **SPSR** (***Saved Program Status Register***)?
     O CPSR armazena o estado atual do processador durante a execução do programa, e o SPSR é temporario para salvar o estado do processador antes que ele seja alterado por uma execução ou interrupção. 

### (f) Qual a finalidade do **LR** (***Link Register***)?
     Serve para armazena o endereço de retorno de uma função, que permite que o programa volte a instrução de chamada quando concluir a sub-rotina ou função.

### (g) Qual o propósito do Program Status Register (PSR) nos processadores ARM?
     Ele serve para armazena informações sonbre o estado atual do processador e informações importantes para o controle e o gerenciamento do processador.

### (h) O que é a tabela de vetores de interrupção?
     É uma tabela que mapeia os endereçoes de entrada de todas as interrupções suportadas pelo processador.

### (i) Qual a finalidade do NVIC (**Nested Vectored Interrupt Controller**) nos microcontroladores ARM e como ele pode ser utilizado em aplicações de tempo real?
    

### (j) Em modo de execução normal, o Cortex-M pode fazer uma chamada de função usando a instrução **BL**, que muda o **PC** para o endereço de destino e salva o ponto de execução atual no registador **LR**. Ao final da função, é possível recuperar esse contexto usando uma instrução **BX LR**, por exemplo, que atualiza o **PC** para o ponto anterior. No entanto, quando acontece uma interrupção, o **LR** é preenchido com um valor completamente  diferente,  chamado  de  **EXC_RETURN**.  Explique  o  funcionamento  desse  mecanismo  e especifique como o **Cortex-M** consegue fazer o retorno da interrupção. 

### (k) Qual  a  diferença  no  salvamento  de  contexto,  durante  a  chegada  de  uma  interrupção,  entre  os processadores Cortex-M3 e Cortex M4F (com ponto flutuante)? Descreva em termos de tempo e também de uso da pilha. Explique também o que é ***lazy stack*** e como ele é configurado. 


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
