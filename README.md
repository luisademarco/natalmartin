<p align="center">
  <img src="capa.jpg" alt="The Martins' Christmas" width="360">
</p>

<h1 align="center">🎄 Amigo secreto dos Martin</h1>

<p align="center">
  O app oficial do amigo secreto de Natal da família Martin.<br>
  Cada um recebe seu próprio link, abre o presente e descobre quem tirou.<br>
  <b>Bico calado até a troca! 🤫</b>
</p>

<p align="center">
  <img src="familia.jpg" alt="Opa, Oma, Tina, Alessandro, Lua, Juan, Teteu, Débora, Daniel, Babi, Luli, Manu e Dé" width="100%">
</p>

## 🎁 Quem participa

Opa, Oma, Tina, Alessandro, Lua, Juan, Teteu, Débora, Daniel, Babi, Luli, Manu e Dé.

## ✨ Como funciona

1. A organizadora abre o site e toca em **Fazer o sorteio**.
2. Cada pessoa recebe no privado um link só dela.
3. Ao abrir o link, a pessoa vê a própria foto, toca no presente e descobre quem tirou, com foto, nome e uma chuva de confete.
4. As apresentações e listas de desejos ficam no grupo da família, pra ninguém errar no presente.

## 📜 Regras

- Ninguém tira a si mesmo.
- Casais podem se tirar.
- Não vale espiar o link dos outros.
- Não vale contar pra ninguém quem tirou.

## 🛠️ Por dentro

Uma única página estática (`index.html`) em HTML, CSS e JavaScript puro: sem framework, sem servidor e sem banco de dados. Fotos e logo vão embutidas no próprio arquivo, e o site é servido pelo GitHub Pages.

### 🎲 O sorteio

O amigo secreto é, matematicamente, um **desarranjo**: uma permutação dos participantes em que ninguém fica na própria posição, ou seja, ninguém tira a si mesmo.

1. **Embaralhamento Fisher–Yates.** A lista de participantes é embaralhada com o algoritmo de Fisher–Yates, que gera todas as ordens possíveis com a mesma probabilidade.
2. **Aleatoriedade criptográfica.** Os números vêm de `crypto.getRandomValues`, o gerador seguro do navegador, com amostragem por rejeição para eliminar o viés de módulo.
3. **Rejeição até virar desarranjo.** Se alguma pessoa cair em si mesma, a permutação é descartada e o embaralhamento recomeça. Cerca de 1 em cada *e* ≈ 2,72 tentativas já é válida, então o sorteio sai em poucas rodadas. Como cada permutação é igualmente provável, todos os desarranjos válidos também são: com 13 pessoas, são **2.290.792.932** sorteios possíveis.

### 🔗 Os links

Cada pessoa recebe um link com um código no fragmento da URL (a parte depois do `#`), por exemplo `#s-k3x9q2a`.

- O código guarda **quem é a pessoa** e **quem ela tirou**, combinados com um *salt* aleatório de 4 caracteres em base 36 e um dígito verificador que detecta links cortados ou alterados.
- O fragmento **nunca é enviado ao servidor**: o navegador lê e decodifica tudo localmente, então nem o GitHub fica sabendo quem tirou quem.
- É uma ofuscação, não uma criptografia: serve para ninguém descobrir o resultado olhando o link, o que é mais do que suficiente para um amigo secreto de família.

A organizadora guarda o sorteio no `localStorage` do próprio navegador, o que permite reenviar um link perdido sem sortear de novo.

### ✨ Experiência

- **Revelação animada:** presente que treme, tampa que voa, raios girando com `conic-gradient` e uma roleta de rostos que desacelera em curva cúbica até parar em quem a pessoa tirou.
- **Confete e neve** desenhados em `<canvas>` com física simples (gravidade, atrito e rotação).
- **Música e efeitos sonoros** sintetizados em tempo real com a **Web Audio API**: "Jingle Bells" (domínio público) em timbre de caixinha de música, com agendamento antecipado das notas para não atrasar, sem nenhum arquivo de áudio.
- **Contagem regressiva** ao vivo até a troca.
- **Acessível e responsivo:** tema claro e escuro automático, respeito ao modo de reduzir movimento do sistema, foco visível no teclado e layout pensado para celular.

---

<p align="center">Feito com carinho pela Luli para o Natal de 2026 🎅</p>
