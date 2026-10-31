# CLAUDE.md

Orientações para o Claude Code neste repositório.

## Sobre o projeto

Projeto pessoal de estudo de latim baseado na *Gramática Latina — Curso Único e Completo*, de Napoleão Mendes de Almeida (29ª ed., Saraiva, 2000). Não há código: o conteúdo é material de estudo em Markdown.

- `plano-de-estudo.md`: plano de 6 meses (26 semanas, 2 nov 2026 a 2 mai 2027) cobrindo as 104 lições, com controle de progresso no final.
- `Gramática Latina.pdf`: o livro digitalizado (552 páginas, ~70 MB). **Não deve ser versionado nem redistribuído** (obra protegida por direitos autorais).

## Idioma e tom

- Responda sempre em **português do Brasil**.
- O usuário é estudante, não especialista. Explique a gramática com clareza e relacione as funções sintáticas latinas ao português, como faz o autor.
- Siga a terminologia do livro: *nominativo, genitivo, dativo, acusativo, vocativo, ablativo*; *tempos primitivos*; *sujeito acusativo*; *agente da passiva*; *consecutio temporum* etc.
- Use a **pronúncia tradicional** (a adotada pelo autor), não a "restaurada".

## Como ler o PDF

- O `Read` não aceita o PDF inteiro (muito grande). Extraia o texto com `pdftotext` (já instalado em `/mingw64/bin`), sempre com `-enc UTF-8`, e salve no scratchpad, nunca no repositório:
  ```bash
  pdftotext -enc UTF-8 -layout "Gramática Latina.pdf" "<scratchpad>/livro.txt"
  ```
- Cada página do PDF é separada por form feed (`\f`). Para pegar uma página: `awk 'BEGIN{RS="\f"} NR==<pág. PDF>' livro.txt`.
- O texto vem de OCR e tem ruído: títulos como "LIÇÃO" saem deformados ("Lrçxo", "LIçoÃ"), e há acentos e números trocados. Não confie em grep por títulos de lição; use o mapa de páginas abaixo. Quando a precisão importar (paradigmas, exemplos), confira lendo a página como imagem com `Read` + `pages`.
- O `pypdf` **não** está instalado.

## Paginação

**Página do PDF = página do livro + 1.** Isso já foi conferido nas lições 1, 65, 77 e 104. O plano mostra as duas no formato `livro / PDF`.

Página inicial (no livro) de cada lição:

| L | pág | L | pág | L | pág | L | pág | L | pág | L | pág | L | pág | L | pág |
|---|---|---|---|---|---|---|---|---|---|---|---|---|---|---|---|
| 1 | 13 | 14 | 53 | 27 | 105 | 40 | 166 | 53 | 230 | 66 | 287 | 79 | 346 | 92 | 417 |
| 2 | 16 | 15 | 56 | 28 | 108 | 41 | 173 | 54 | 233 | 67 | 293 | 80 | 353 | 93 | 422 |
| 3 | 18 | 16 | 59 | 29 | 114 | 42 | 177 | 55 | 237 | 68 | 295 | 81 | 357 | 94 | 424 |
| 4 | 23 | 17 | 61 | 30 | 120 | 43 | 183 | 56 | 241 | 69 | 302 | 82 | 362 | 95 | 428 |
| 5 | 25 | 18 | 65 | 31 | 127 | 44 | 186 | 57 | 246 | 70 | 306 | 83 | 368 | 96 | 434 |
| 6 | 28 | 19 | 69 | 32 | 130 | 45 | 190 | 58 | 251 | 71 | 309 | 84 | 374 | 97 | 440 |
| 7 | 31 | 20 | 72 | 33 | 135 | 46 | 194 | 59 | 256 | 72 | 313 | 85 | 379 | 98 | 447 |
| 8 | 34 | 21 | 77 | 34 | 139 | 47 | 197 | 60 | 260 | 73 | 318 | 86 | 387 | 99 | 451 |
| 9 | 37 | 22 | 81 | 35 | 142 | 48 | 203 | 61 | 264 | 74 | 323 | 87 | 391 | 100 | 459 |
| 10 | 41 | 23 | 85 | 36 | 149 | 49 | 208 | 62 | 268 | 75 | 328 | 88 | 398 | 101 | 463 |
| 11 | 44 | 24 | 89 | 37 | 154 | 50 | 212 | 63 | 274 | 76 | 332 | 89 | 403 | 102 | 471 |
| 12 | 46 | 25 | 94 | 38 | 158 | 51 | 216 | 64 | 277 | 77 | 335 | 90 | 407 | 103 | 478 |
| 13 | 49 | 26 | 98 | 39 | 161 | 52 | 222 | 65 | 283 | 78 | 341 | 91 | 413 | 104 | 483 |

Outras referências: Prefácio pág. 7 · Índice Geral págs. 7–8 do PDF · Índice Alfabético e Analítico pág. 497 · Referências pág. 531.

## Estrutura do livro

- **L1–47:** parte nominal (casos, 5 declinações, adjetivos, numerais, pronomes, noções das conjugações).
- **L48–76:** o verbo (conjugação ativa e passiva, *sum*, depoentes, irregulares, defectivos, impessoais, composição e derivação).
- **L77–104:** sintaxe do período (*consecutio temporum*, discurso indireto, subordinadas e coordenadas) com leitura de César, Cícero, Fedro, Virgílio, Horácio, Ovídio, Eutrópio e Valério Máximo.
- Cada lição tem questionário; a maioria tem 2 exercícios numerados (Exs. 1–114 no total).

## Convenções do plano de estudo

- As tabelas semanais seguem o formato `| Dia | Conteúdo | Págs. (livro / PDF) |`, de segunda a sexta, com o sábado para revisão.
- Os feriados brasileiros são folgas. Se as datas mudarem, recalcule os feriados móveis (Carnaval e Sexta-feira Santa dependem da Páscoa).
- O progresso é marcado na lista "Controle de progresso" (`- [ ]` → `- [x]`). Quando o usuário relatar progresso, atualize essa lista.

## Direitos autorais

Não reproduza trechos longos do livro em arquivos do repositório. Resumos, quadros de paradigmas feitos pelo usuário e referências de página são aceitáveis; transcrições extensas, não.
