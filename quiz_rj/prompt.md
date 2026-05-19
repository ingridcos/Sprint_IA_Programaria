# 🤖 Prompt usado para gerar o jogo

Este arquivo documenta o prompt utilizado para criar o Quiz Rio de Janeiro com o Claude (Anthropic).

---

## Prompt inicial

```
Crie um jogo interativo sobre os pontos turísticos do Rio de Janeiro com as seguintes especificações:

Tema e visual:
* Tema carioca: cores do Rio (verde, amarelo, azul do céu e do mar)
* Fundo com ilustração simples da skyline do Rio (Cristo, Pão de Açúcar, prédios)
* Fonte moderna e legível, interface toda em português

Mecânica do jogo:
* Quiz com 15 perguntas divididas em 3 fases
* Fase 1: "Onde fica?" — localização dos pontos turísticos
* Fase 2: "Qual é qual?" — características e curiosidades
* Fase 3: "Você sabe de verdade?" — perguntas difíceis
* Cada acerto vale 10 pontos
* Mostrar feedback após cada resposta (certo/errado + curiosidade sobre o local)
* Perguntas em ordem aleatória a cada partida

Pontos turísticos que devem aparecer no jogo:
Cristo Redentor, Pão de Açúcar, Mureta da Urca, Aterro do Flamengo, Lapa, Santa Teresa,
Parque das Ruínas, Copacabana, Ipanema, Leblon, Vidigal, Morro Dois Irmãos, Pedra Bonita,
Barra da Tijuca, Floresta da Tijuca e Vista Chinesa.

Telas do jogo:
* Tela inicial com título e botão "Começar"
* Tela de pergunta com: emoji do local, pergunta, 4 opções de resposta, barra de progresso e pontuação
* Tela de feedback após cada resposta com curiosidade sobre o local
* Tela final com pontuação total, classificação e botão "Jogar novamente"

Classificação final:
* 150 pontos: "Carioca da gema e de coração!"
* 100–140 pontos: "Quase local!"
* 60–90 pontos: "Turista em evolução"
* Abaixo de 60: "Bora conhecer o Rio?"

Tecnologia: HTML, CSS e JavaScript puro em um único arquivo index.html
```

---

## Correções feitas após o prompt inicial

Durante os testes, dois bugs foram identificados e corrigidos:

**Bug 1 — Pontuação errada**
O jogo marcava respostas corretas como erradas porque as opções eram embaralhadas visualmente, mas o código comparava a posição clicada com o índice original da resposta. A correção foi rastrear a nova posição da resposta correta após o embaralhamento.

**Bug 2 — Fase 2 travava**
Ao clicar em "Vamos lá!" na tela de transição da Fase 2, o jogo entrava em loop e não avançava. O problema era que a detecção de mudança de fase usava o índice da pergunta anterior, então após a transição ser exibida, ela era detectada novamente. A correção foi usar `estado.faseAtual` como controle, atualizado no momento em que a transição é exibida.

---

## Ferramenta utilizada

- **IA:** Claude Sonnet (Anthropic) — claude.ai e Replit
- **Vibecoding:** o prompt descreveu o produto desejado; a IA gerou e corrigiu o código
