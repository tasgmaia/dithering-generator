# dither-chars

Transforma uma imagem ou um vídeo em dithering ordenado (matriz de Bayer) desenhando caracteres personalizados em vez de pixels.

## Como rodar

Abra `index.html` no navegador. Não há build nem dependências.

Opcional, com servidor local:

```bash
npx serve .
# ou
python3 -m http.server 8000
```

## Recursos

- Upload de imagem ou vídeo (botão ou arrastar e soltar)
- Vídeo com prévia em tempo real e download do vídeo inteiro processado em MP4 (ou WebM, conforme o navegador)
- Modo dithering (1 bit) e modo rampa de caracteres (ASCII)
- Caracteres dos pontos editáveis, com presets e ordem alternada, aleatória, texto contínuo (uma frase flui pelos pontos) ou por tom (o software mede a densidade de cada caractere e usa os mais cheios nos tons mais fortes; também disponível na rampa)
- Cor da imagem original nos caracteres e no fundo (escurecido)
- Tamanho da célula, contraste, brilho, matriz de Bayer (2×2, 4×4, 8×8)
- Resposta ao tom: liga/desliga (Bayer) ou caracteres que variam de tamanho e/ou opacidade conforme o tom, com ajuste de sensibilidade
- Fonte, cor de fundo, cor dos caracteres e inversão
- Botão para resetar as configurações
- Zoom na prévia (roda do mouse, pinça, botões ou teclas + − 0) e arrastar para mover
- Exportação em PNG e SVG

## Estrutura

- `index.html`: página única com HTML, CSS e JavaScript.
