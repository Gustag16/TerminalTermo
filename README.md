# Termo no Terminal

Neste repositório, encontra-se uma simulação via terminal do popular jogo de adivinhação de palavras (inspirado no Wordle), desenvolvido totalmente em C

O objetivo é descobrir uma palavra secreta de cinco letras em até **6 tentativas**. A cada palpite, o jogo fornece um feedback visual colorido indicando o quão perto você está da resposta correta.

---

## Funcionalidades

O jogo foi aprimorado com diversas funções para melhorar a experiência do usuário no terminal:

*  **Dois Modos de Jogo:**
   * **Termo Aleatório:** O jogo sorteia uma palavra do banco de dados automaticamente.
   * **Termo com Amigos:** Um jogador digita uma palavra secreta (que é ocultada da tela) para que o outro jogador tente adivinhar.
*  **Normalização Inteligente de Texto:** Não se preocupe com o Caps Lock ou acentuação. O programa aceita letras minúsculas e remove acentos (á, ç, õ, etc) automaticamente em tempo real usando formatação UTF-8.
*  **Interface Colorida e Dinâmica:** Utiliza códigos de escape ANSI para colorir as letras e manipula o cursor do terminal para apagar linhas, criando uma interface limpa sem poluir o histórico do terminal.
*  **Validação de Palavras:** O sistema cruza sua tentativa com um banco de dados (`possiveis_entradas_usuario.txt`) para garantir que você digite apenas palavras válidas na língua portuguesa.

---

## Como Jogar

1. Escolha o modo de jogo no menu inicial.
2. Digite um palpite de 5 letras. O jogo contabiliza a entrada e diminui suas tentativas restantes.
3. O terminal retornará as letras digitadas com as seguintes cores:
   * 🟩 **VERDE:** A letra faz parte da palavra e está na **posição correta**.
   * 🟨 **AMARELA:** A letra faz parte da palavra, mas está na **posição errada**.
   * 🟥 **VERMELHA:** A letra **não faz parte** da palavra.
4. Você vence se acertar a palavra (5 letras verdes) dentro das 6 tentativas permitidas.

### Exemplo de Partida

Supondo que a palavra secreta seja **AVIAO**:

```text
Digite uma palavra:
AUREO
[A] [U] [R] [E] [O]      Tentativas restantes: 5  (U, R, E em vermelho)

ABACO
[A] [B] (A) [C] [O]      Tentativas restantes: 4  (A central em amarelo)

ARPAO
[A] [R] [P] [A] [O]      Tentativas restantes: 3  (R, P em vermelho)

AVIAO
[A] [V] [I] [A] [O]      (Tudas as letras verdes)

Parabéns!!! Você acertou!!!
```

---

## Estrutura de Arquivos

Para que o jogo funcione corretamente, os seguintes arquivos devem estar no mesmo diretório:

* `termo.c`: O código-fonte principal do jogo.
* `possiveis_palavras_chave.txt`: Banco com as possíveis palavras que o jogo irá sortear (gabaritos).
* `possiveis_entradas_usuario.txt`: Dicionário amplo contendo todas as palavras aceitas como tentativa.

---

## Como Executar

**Pré-requisitos:** O jogo utiliza as bibliotecas `<termios.h>` e `<unistd.h>`, sendo voltado para sistemas operacionais baseados em Unix (**Linux, macOS ou WSL no Windows**). Um compilador C (como o GCC) é necessário.

1. Clone o repositório:
```bash
git clone https://github.com/Gustag16/Termo.git
```

2. Acesse a pasta do projeto:
```bash
cd Termo
```

3. Compile o código-fonte usando o GCC:
```bash
gcc termo.c -o termo
```

4. Execute o jogo:
```bash
./termo
```

---
*Gustag16*
