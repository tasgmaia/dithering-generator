# dither-chars

Ferramenta web de arte generativa: imagem ou vídeo para dithering de Bayer com caracteres personalizados.

## Stack e convenções

- Um único `index.html` (HTML + CSS + JS vanilla), sem build e sem dependências (só as fontes Barlow e Nanum Myeongjo via Google Fonts, com fallback).
- Idioma da interface: português do Brasil.
- Renderização em `<canvas>` na função `render()`: a imagem é reduzida para uma grade (uma célula por caractere), o brilho de cada célula é comparado com a matriz de Bayer e o caractere é desenhado com `fillText`.
- Controles ficam na `<aside>`; todo controle novo deve chamar `render()` e ter seu valor padrão em `DEFAULTS` (usado pelo botão de resetar).
- Estilo: tokens do "Meu portfolio DS" em `:root`, com os mesmos nomes de `../src/styles/global.css` (`--color-ac1`, `--color-paper`, `--color-ink`, `--color-gray-*`, `--font-sans`, `--font-serif`); não use cor solta, use um token, tema claro fixo (`color-scheme: light`); todo botão e campo define `color: var(--color-ink)` para não herdar a cor do navegador.
- Cada item desenhado também vai para `scene.items`, que `toSVG()` usa na exportação SVG; todo desenho novo em `render()` precisa ser registrado lá.
- Vídeo: `img` passa a ser o `<video>` e `tick()` chama `render()` a cada quadro novo; o botão "Baixar vídeo" toca o vídeo do início ao fim gravando `out.captureStream()` com `MediaRecorder`. Por isso `render()` precisa ser rápida: nada de criar canvas ou mudar `out.width` a cada chamada.
- Zoom da prévia: só um `transform` CSS em `#stage` (estado em `view`); não mexe em `out.width` nem nas exportações.
