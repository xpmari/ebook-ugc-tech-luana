---
name: ebook-ugc-tech
description: Regras de design e montagem do ebook "UGC TECH DO ZERO" (estilo Pinterest, paleta roxo/lilás/laranja/terracota/branco, exportado em PDF para o Cakto). Use SEMPRE que o usuário pedir para criar, montar, editar ou revisar qualquer página, capa, capítulo, checklist, mockup ou elemento visual deste ebook, mesmo que ele não diga "skill" ou "ebook" explicitamente (ex.: "faz a capa", "monta o capítulo 3", "cria a página da autora", "exporta o PDF").
---

# Ebook "UGC TECH DO ZERO" — Guia de design e montagem

## 1. Contexto

- **Projeto:** ebook digital sobre UGC (criação de conteúdo para marcas) na área de tecnologia, para iniciantes.
- **Título:** UGC TECH DO ZERO
- **Subtítulo:** [A DEFINIR COM A CLIENTE — se ainda não foi informado, deixe um placeholder visível e não invente]
- **Tamanho:** 60 a 80 páginas.
- **Entrega:** PDF, vendido pelo Cakto. A maioria dos leitores abre no **celular**.
- **Papel do designer:** a cliente envia todo o conteúdo. O trabalho aqui é **diagramar e dar identidade visual**, não escrever.
- **Idioma:** português do Brasil, com acentuação correta em tudo.

## 2. Regra de ouro sobre o conteúdo

- **Nunca** reescreva, resuma, corrija o sentido ou invente texto da cliente. Pode ajustar apenas quebras de linha, hierarquia (título, subtítulo, corpo) e pontuação óbvia de diagramação.
- Se faltar conteúdo, use um placeholder claro (ex.: `[FOTO DA AUTORA]`, `[PRINT 1 – tela do app]`) em vez de inventar.
- Prints, fotos e imagens vêm da cliente. Nunca gere imagens de pessoas por IA nem use fotos de bancos sem avisar de onde vieram.

## 3. Formato da página

- **Tamanho padrão: 1080 × 1350 px (proporção 4:5, vertical)**, pensado para leitura no celular.
- Se a cliente pedir impressão, o formato muda para A4 (794 × 1123 px). Para trocar, altere só as variáveis `--page-w` e `--page-h` no CSS.
- Margem interna segura: 90 px nas laterais, 100 px em cima e embaixo.
- Cada página é um bloco `<section class="page">` com `break-after: page`.

## 4. Paleta

Defina sempre estas cores como variáveis CSS e use só elas:

```css
:root {
  --bg:        #FAF6F1; /* branco quente — fundo principal (~60%) */
  --roxo:      #4A2C7A; /* roxo profundo — marca, títulos, blocos de cor (~25%) */
  --lilas:     #CDB8EA; /* lilás — apoio, fundos suaves, caixas */
  --laranja:   #F28A30; /* laranja — destaque (~10%) */
  --terracota: #C4623F; /* terracota — detalhes quentes (~5%) */
  --branco:    #FFFFFF;
  --tinta:     #2A1A45; /* roxo quase preto — texto corrido */
}
```

Regras de uso:

- Fundo das páginas: `--bg` na maioria. Alterne com páginas de bloco inteiro em `--roxo` ou `--lilas` para criar ritmo (por exemplo, abertura de capítulo).
- Texto corrido: sempre `--tinta` sobre fundo claro, ou `--bg` sobre `--roxo`.
- **Não use laranja nem terracota como cor de texto corrido** sobre fundo claro (contraste baixo). Use-as em palavras de destaque grandes, selos, setas, marca-texto, fitas e ícones.
- Sobre fundo laranja, o texto deve ser `--tinta` ou `--roxo`, nunca branco.
- Não introduza outras cores (nada de azul, verde, cinza frio). Variações de opacidade das cores acima são permitidas.

## 5. Tipografia

Carregue pelo Google Fonts (e embuta no HTML para não depender de conexão na exportação, se possível):

- **Títulos:** Fraunces (peso 600–800, itálico permitido para palavras de destaque).
- **Texto corrido:** DM Sans (400 e 500, 700 para negrito).
- **Anotações à mão** (rabiscos, setas com texto, post-its): Caveat.

Tamanhos mínimos para leitura no celular, na página de 1080 px de largura:

- Texto corrido: **34 a 38 px**, entrelinha 1.5.
- Subtítulos: 52 a 64 px.
- Títulos de capítulo: 110 a 180 px.
- Nada de texto menor que 28 px, nem em legendas.
- Máximo de ~45 caracteres por linha no corpo do texto; parágrafos curtos.

Não use Inter, Roboto, Arial nem Poppins.

## 6. Estilo visual: "Pinterest", feito por humano

A cliente quer um ebook **intuitivo, com cara de moodboard Pinterest**, e que **não pareça feito por IA**.

**Faça:**

- Colagem: fotos recortadas com contorno branco grosso e sombra suave, polaroids levemente inclinadas (-3° a 3°), fita adesiva (washi tape), post-its, clipes.
- Detalhes à mão: setas, círculos e sublinhados desenhados em SVG com traço irregular; marca-texto em cima de palavras-chave; anotações em Caveat.
- Blocos de tamanhos diferentes, cantos bem arredondados (24 a 40 px), cartões que se sobrepõem um pouco.
- Texturas sutis de papel ou grão (CSS ou SVG de baixa opacidade) nos fundos.
- Muito respiro. Cada página tem **um foco** claro.
- Numeração de página discreta, e um elemento de navegação consistente (ex.: título do capítulo no topo, em letra pequena).
- Ícones simples, de traço, no mesmo estilo e espessura em todo o ebook.

**Evite (isso entrega "cara de IA"):**

- Degradê roxo-azulado genérico e brilhos (glow).
- Emojis usados como ícones.
- Grade de cartões todos iguais, perfeitamente simétricos e centralizados em todas as páginas.
- Sombras e bordas iguais em tudo, "glassmorphism", neon.
- Ilustrações geradas por IA e fotos de banco com cara de "pessoas sorrindo no escritório".
- Textos em caixa alta em excesso e travessões longos decorativos.
- Repetir o mesmo layout em páginas seguidas.

Regra prática: **imperfeição controlada**. Pequenas inclinações, sobreposições e assimetrias, mas sempre dentro da mesma paleta, das mesmas fontes e da mesma margem.

## 7. Modelos de página (componentes)

Construa e reutilize estes modelos. Varie a composição dentro de cada um para não ficar repetitivo.

1. **Capa:** título grande "UGC TECH DO ZERO", subtítulo, colagem (foto da autora recortada, elementos tech como notebook ou celular, selos, fita). Fundo `--roxo` ou `--lilas`.
2. **Sumário:** lista de capítulos com número grande e página, estilo índice de revista.
3. **Abertura de capítulo:** página inteira em cor, número do capítulo enorme, título, uma frase curta de abertura.
4. **Texto:** título, parágrafos curtos, uma palavra-chave com marca-texto, uma anotação em Caveat.
5. **Checklist:** caixas de seleção desenhadas, lista com itens curtos, cartão em `--lilas`.
6. **Destaque / dica / atenção:** bloco colorido com ícone e post-it, ocupando metade da página.
7. **Passo a passo:** números grandes (1, 2, 3…) com linha ou seta conectando os passos.
8. **Prints e mockup:** moldura de celular ou notebook com o print da cliente, legendas em Caveat com setas.
9. **Citação / frase de impacto:** página com uma única frase grande em Fraunces itálico.
10. **Sobre a autora:** foto recortada com contorno, texto de apresentação, três "curiosidades" em post-its.
11. **Conclusão e agradecimentos:** página mais calma, com respiro.
12. **Contatos:** redes sociais e link, com ícones e um chamado final.

## 8. Estrutura técnica (HTML/CSS → PDF)

- Arquivos: um `index.html` com as páginas na ordem, ou um arquivo por capítulo importado no principal. CSS em `styles.css`. Imagens em `/assets`.
- CSS base obrigatório:

```css
@page { size: 1080px 1350px; margin: 0; }
.page {
  width: var(--page-w, 1080px);
  height: var(--page-h, 1350px);
  position: relative;
  overflow: hidden;
  break-after: page;
  page-break-after: always;
  -webkit-print-color-adjust: exact;
  print-color-adjust: exact;
}
```

- Nada de conteúdo que transborde a página: se o texto não couber, **divida em duas páginas** em vez de diminuir a fonte abaixo do mínimo.
- Imagens: comprimidas (JPG/WebP otimizado, largura máxima ~1600 px). Meta: PDF final leve o bastante para abrir rápido no celular e respeitar o limite de upload do Cakto (confirmar o limite atual na plataforma).
- Textos selecionáveis no PDF (não transformar texto em imagem).
- Exportação: abrir no Chrome, Imprimir, Salvar como PDF, tamanho personalizado igual ao da página, margens "nenhuma", ativar "gráficos de plano de fundo".
- Links (redes sociais, site) devem ser clicáveis no PDF.

## 9. Fluxo de trabalho obrigatório

1. **Não monte as 60–80 páginas de uma vez.** Primeiro crie só: capa, sumário, abertura de capítulo, texto, checklist, caixa de destaque, página de prints/mockup, sobre a autora e contato, usando textos de exemplo.
2. Pare e peça aprovação da designer/cliente sobre esse primeiro conjunto.
3. Com a aprovação, receba o conteúdo real e diagrame **capítulo por capítulo**, mostrando cada capítulo antes de seguir.
4. Ao final, faça a revisão (checklist abaixo) e exporte o PDF.

## 10. Checklist final antes de exportar

- [ ] Só existem as cores da paleta.
- [ ] Só existem as 3 fontes definidas.
- [ ] Nenhum texto menor que 28 px; corpo entre 34 e 38 px.
- [ ] Nenhum texto cortado ou fora da margem segura.
- [ ] Nenhuma página repete exatamente o layout da anterior.
- [ ] Nenhum emoji usado como ícone, nenhum degradê genérico, nenhum glow.
- [ ] Texto da cliente intacto, sem invenções; placeholders sinalizados.
- [ ] Numeração das páginas e sumário conferem.
- [ ] Legibilidade testada em tela pequena (visualizar a 40% de zoom).
- [ ] PDF leve, com texto selecionável e links funcionando.
