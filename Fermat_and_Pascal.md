# Origem Histórica da Teoria das Probabilidades: Pascal e Fermat

A teoria das probabilidades tem suas origens no século XVII, impulsionada pela correspondência entre dois matemáticos franceses, Blaise Pascal e Pierre de Fermat. Esse desenvolvimento ocorreu a partir de problemas relacionados a jogos de azar, os quais motivaram o estudo matemático das incertezas.

---

## O Problema dos Pontos

Em 1654, o nobre e jogador Antoine Gombaud, conhecido como Chevalier de Méré, apresentou a Pascal um problema clássico de jogos de azar: como dividir justamente as apostas entre jogadores quando um jogo é interrompido antes de seu término? Esse problema, conhecido como "Problema dos Pontos", despertou o interesse de Pascal, que iniciou uma troca de cartas com Fermat para resolvê-lo.

O problema pode ser descrito assim: dois jogadores A e B estão jogando uma série de partidas e concordam que o vencedor será aquele que primeiro atingir um número predefinido de vitórias. No entanto, o jogo é interrompido antes de ser concluído, e os jogadores desejam dividir a aposta proporcionalmente às suas chances de vencer caso o jogo tivesse continuado.

Por exemplo, suponha que o jogo é uma melhor de 5 partidas (ou seja, o primeiro a ganhar 3 partidas vence). Se A já ganhou 2 rodadas e B ganhou 1, como dividir a aposta de maneira justa?

---

## A Solução de Pascal

Blaise Pascal desenvolveu uma abordagem baseada na distribuição das chances futuras. Ele percebeu que, para dividir o prêmio de forma justa, era necessário calcular todas as possibilidades restantes e determinar a proporção de vitórias prováveis para cada jogador.

No exemplo do jogo melhor de 5, restam no máximo duas partidas a serem jogadas. Se A vencer a próxima partida, ele ganha o jogo imediatamente. Se B vencer a próxima, então a disputa ficará empatada, e será necessário jogar a última partida para decidir o vencedor.

Pascal listou os cenários restantes:

- Se A vencer a próxima partida (probabilidade de 1/2), ele ganha o jogo imediatamente.
- Se B vencer a próxima partida (probabilidade de 1/2), o jogo continua para uma última decisiva.
- Na última partida, cada jogador tem novamente 1/2 de chance de vencer.

As probabilidades de vitória são:

- Para A: \(P(A) = 1/2 + (1/2 	* 1/2) = 3/4\)
- Para B: \(P(B) = (1/2 	* 1/2) = 1/4\)

Assim, Pascal concluiu que a aposta deveria ser dividida na proporção de 3:1 a favor de A.

---

## A Solução de Fermat

Pierre de Fermat abordou o problema de forma diferente, mas chegou ao mesmo resultado. Ele propôs considerar todas as sequências possíveis que poderiam ocorrer até o fim do jogo e contar quantas dessas sequências resultavam na vitória de A ou de B.

No exemplo acima, as partidas restantes poderiam se desenrolar assim:

1. A vence imediatamente (A ganha, jogo termina).
2. B vence a próxima, e depois A vence (B ganha, A ganha).
3. B vence a próxima e também vence a última (B ganha, B ganha).

As três sequências possíveis são:

- A vence diretamente.
- B vence e depois A vence.
- B vence duas vezes seguidas.

Dessas três possibilidades, A vence em 2 delas e B vence em apenas 1. Assim, a razão de vitória é 2:1, o que corresponde a 3/4 para A e 1/4 para B, confirmando a solução de Pascal.

---

## Impacto e Desenvolvimento Posterior

A abordagem de Pascal e Fermat marcou o início da teoria das probabilidades e foi a primeira tentativa de modelar matematicamente a incerteza. Esse desenvolvimento influenciou matemáticos posteriores como Christiaan Huygens, Jakob Bernoulli e Pierre-Simon Laplace, que expandiram a teoria para novas áreas.

O impacto dessas descobertas foi profundo, pois a teoria das probabilidades passou a ser aplicada não apenas em jogos de azar, mas também na estatística, na economia, na ciência atuarial e até mesmo na inteligência artificial e machine learning modernos.

O legado de Pascal e Fermat continua presente, e seu trabalho pioneiro permitiu que a probabilidade se tornasse uma das ferramentas matemáticas mais poderosas para a tomada de decisões sob incerteza.

