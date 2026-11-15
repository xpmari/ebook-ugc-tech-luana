---
name: ebook-ugc-tech
description: Regras de design e montagem do ebook "UGC TECH DO ZERO" (estilo Pinterest, paleta ameixa/terracota/laranja/verde oliva/vinho/off white, exportado em PDF para o Cakto). Use SEMPRE que o usuário pedir para criar, montar, editar ou revisar qualquer página, capa, capítulo, checklist, mockup ou elemento visual deste ebook, mesmo que ele não diga "skill" ou "ebook" explicitamente (ex.: "faz a capa", "monta o capítulo 3", "cria a página da autora", "exporta o PDF").
---

# Ebook "UGC TECH DO ZERO" — Guia de design e montagem

## 1. Contexto

- **Projeto:** ebook digital sobre UGC (criação de conteúdo para marcas) na área de tecnologia, para iniciantes.
- **Título:** UGC TECH DO ZERO
- **Subtítulo:** Do primeiro cadastro às campanhas internacionais
- **Autora:** Luana (perfil "Luana | UGC Tech Creator")
- **Público:** mulheres brasileiras que querem criar conteúdo para aplicativos e plataformas, mesmo começando do zero e sem falar inglês.
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

## 4. Paleta (oficial, enviada pela cliente)

A cliente enviou uma paleta própria (arquivo `referencias/paleta-moodboard-figos.png`). **Ela vale mais do que qualquer outra cor.** Defina sempre estas variáveis CSS e use só elas:

```css
:root {
  --bg:        #F8F6F1; /* Off White — fundo principal (~55%) */
  --ameixa:    #7B559A; /* Ameixa — cor de marca, títulos, blocos de cor (~25%) */
  --terracota: #D15905; /* Terracota — destaque quente (~8%) */
  --laranja:   #F57C00; /* Laranja — destaque forte, usar pouco (~5%) */
  --oliva:     #688C3E; /* Verde Oliva — detalhe pontual, ex.: checklist, "ok" (~3%) */
  --vinho:     #751842; /* Vinho — fundos escuros, ênfase, contraste (~4%) */

  /* Derivadas permitidas (tons mais claros ou mais escuros das cores acima) */
  --ameixa-clara: #D9CCE6; /* tom claro da ameixa, para caixas e fundos suaves */
  --tinta:        #2E1F3D; /* tom bem escuro da ameixa, para texto corrido */
  --branco:       #FFFFFF;
}
```

Regras de uso:

- Fundo das páginas: `--bg` na maioria. Alterne com páginas de bloco inteiro em `--ameixa`, `--vinho` ou `--ameixa-clara` para criar ritmo (por exemplo, aberturas de capítulo).
- Texto corrido: `--tinta` sobre fundo claro; `--bg` sobre `--ameixa` ou `--vinho`.
- **Contraste:** terracota, laranja e oliva sobre fundo claro só para texto **grande** (títulos, números, palavras de destaque) ou para formas, selos, setas e marca-texto. Nunca para texto corrido.
- Sobre fundo laranja ou terracota, texto em `--tinta` ou `--bg`, conferindo a leitura.
- **Verde oliva e vinho existem na paleta da cliente**: use com moderação, em pontos específicos, sem deixar a página parecer natalina (evite vinho + oliva lado a lado em grandes áreas).
- Não introduza cores fora da paleta (nada de azul, rosa-chiclete, cinza frio). Variações de opacidade são permitidas.
- As fotos da cliente têm fundo **lilás**; combine-as com `--ameixa` e `--ameixa-clara`.

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

- Degradê roxo-azulado genérico (a ameixa é cor chapada, não degradê) e brilhos (glow).
- Emojis usados como ícones.
- Grade de cartões todos iguais, perfeitamente simétricos e centralizados em todas as páginas.
- Sombras e bordas iguais em tudo, "glassmorphism", neon.
- Ilustrações geradas por IA e fotos de banco com cara de "pessoas sorrindo no escritório".
- Textos em caixa alta em excesso e travessões longos decorativos.
- Repetir o mesmo layout em páginas seguidas.

Regra prática: **imperfeição controlada**. Pequenas inclinações, sobreposições e assimetrias, mas sempre dentro da mesma paleta, das mesmas fontes e da mesma margem.

## 7. Modelos de página (componentes)

Construa e reutilize estes modelos. Varie a composição dentro de cada um para não ficar repetitivo.

1. **Capa:** título grande "UGC TECH DO ZERO", subtítulo, colagem (foto da autora recortada, elementos tech como notebook ou celular, selos, fita). Fundo `--ameixa` ou `--ameixa-clara`.
2. **Sumário:** lista de capítulos com número grande e página, estilo índice de revista.
3. **Abertura de capítulo:** página inteira em cor, número do capítulo enorme, título, uma frase curta de abertura.
4. **Texto:** título, parágrafos curtos, uma palavra-chave com marca-texto, uma anotação em Caveat.
5. **Checklist:** caixas de seleção desenhadas, lista com itens curtos, cartão em `--ameixa-clara`, marcas de "feito" em `--oliva`.
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

## 8.1 Material recebido da cliente

**Conteúdo:** `conteudo/ugc-tech-do-zero.md` (~6.600 palavras, 26 capítulos, 9.x e 19.x com subtópicos, kit de modelos, glossário e considerações finais). Esse arquivo é a **fonte única do texto**. Estimativa: 60 a 80 páginas no formato 1080×1350.

Como tratar o arquivo de texto:

- A linha `⸻` é só um separador do documento original: **não aparece no ebook**, é só uma pista de quebra de seção.
- `##` numerado = capítulo (abre com página de abertura). `9.1`, `19.1`, `25.1` etc. = subtópicos dentro do capítulo.
- `**Negrito**` do original continua em negrito; listas numeradas viram passo a passo; listas com `*` viram checklist ou lista com marcadores desenhados.
- Modelos de mensagem do Kit (cap. 25) ficam em caixas tipo "cartão copiável", para a leitora poder copiar fácil.
- O glossário (cap. 26) vira cartões ou colunas pequenas, uma página ou duas.
- O sumário do texto não tem números de página: gere o sumário com a numeração real, ao final da diagramação.
- **Não existem no texto**: "Sobre a autora", agradecimentos e contatos. Crie as páginas com placeholders (`[TEXTO SOBRE A AUTORA]`, `[AGRADECIMENTOS]`, `[@ DO INSTAGRAM]`) e **não invente** nenhum conteúdo.

**Imagens** (em `assets/`):

| Arquivo | O que é | Uso sugerido |
|---|---|---|
| `fotos/foto-autora-blusa-lilas.png` (1024×1536) | foto da autora de blusa lilás, segurando o celular | capa e página "sobre a autora" |
| `fotos/foto-autora-terninho-notebook.png` (896×1152) | foto da autora sentada, de terninho lilás, com notebook, fundo lilás | capa, abertura de capítulo e boas-vindas |
| `fotos/avatar-circular-1.png` e `avatar-circular-2.png` | fotos de perfil em círculo, fundo transparente | detalhes pequenos, perfil, rodapé de capítulo |
| `prints/print-coldtrace-fixo-mensal.png` | card de campanha: valor fixo por mês | cap. 19 (Fixed Fee) |
| `prints/print-picsart-cpm.png` | card de campanha: valor por 1.000 views | cap. 19 (CPM) |
| `prints/print-dr-melaxin-fixo-cpm.png` | card: fixo mensal + CPM | cap. 19 (Fixed Fee + CPM) |
| `prints/print-gizmo-por-post.png` | card: valor por post | cap. 19 e cap. 16 |
| `prints/print-wayk-por-ciclo.png` | card: valor por ciclo | cap. 19 e cap. 16 |
| `prints/print-rjb-post-comissao.png` | card: valor por post + comissão sobre anúncios | cap. 19 (comissão) |
| `prints/print-instagram-perfil.png` | print de perfil de Instagram | cap. 12 |
| `prints/print-instagram-bio.png` | print de bio de Instagram | cap. 12 e kit 25.1 |
| `referencias/paleta-moodboard-figos.png` | paleta oficial da cliente | **só referência**, não entra no ebook |

Regras para as imagens:

- Os prints têm resolução baixa (cerca de 770 a 1.290 px de largura). **Não amplie além do tamanho original**: mostre-os dentro de cartões, molduras de celular ou polaroids, com largura máxima de ~800 px.
- Não redesenhe, traduza nem altere logos e textos dos prints. Pode recortar, inclinar levemente, colocar sombra e fita adesiva.
- Se a associação de um print com um capítulo estiver duvidosa, deixe uma legenda neutra e **pergunte antes de decidir**.
- Fotos da autora: não retoque o rosto nem o corpo; só recorte, enquadre e ajuste de cor leve.

## 9. Fluxo de trabalho obrigatório

1. **Não monte as 60–80 páginas de uma vez.** Se as páginas-modelo ainda não foram aprovadas, crie primeiro só: capa, sumário, abertura de capítulo, texto, checklist, caixa de destaque, página de prints/mockup, sobre a autora e contato (com as fotos reais e textos do ebook, ou de exemplo).
2. Pare e peça aprovação da designer/cliente sobre esse primeiro conjunto.
3. Com a aprovação, **leia o conteúdo completo e proponha um plano de paginação** (capítulo → nº de páginas → modelo de página usado), sem montar nada ainda. Espere a aprovação do plano.
3.1. Monte em lotes de 3 a 4 capítulos (comece pela capa, sumário provisório e capítulos 1 a 3), mostrando cada lote antes de seguir. Não resuma nem reescreva o texto para caber: se não couber, crie mais uma página.
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
