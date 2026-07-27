# Teste técnico — Landing page com prompt estruturado (26/07/2026)

Teste derivado da hipótese registrada por Atena em [[../../02_Conhecimento/01_Estudos/youtube-descomplicandosites-landing-page-claude-design|Claude Design e Claude Chat: Como criar Landing Page com IA]], a partir de um vídeo que Mica pediu para a Atena assistir de verdade (não só transcrição). Executado por Lex a pedido direto de Mica, em 26/07/2026.

## O que foi testado

Se a técnica de **prompt estruturado por campos fixos** (cor principal, cor secundária, cor de fundo + estrutura obrigatória: Hero → Benefícios → Oferta → Prova social → FAQ → CTA final) descrita no vídeo funciona também com **Claude Code** (ferramenta que a Ethos já usa, sem custo adicional) e com a **hospedagem gratuita já validada** (GitHub Pages) — em vez do Claude Design + Hostinger (paga) usados no vídeo original.

**Importante:** o conteúdo ("Fisio Vitalis", clínica de fisioterapia) é **fictício**. Nicho escolhido por Lex só para o teste, sem nenhuma implicação de decisão de nicho, oferta ou identidade visual da Ethos Studio — essas decisões continuam pausadas (ver `00_Direcao/CONTEXTO_ATIVO.md`).

## Sobre a parte de hospedagem/domínio (correção de Mica, 26/07/2026)

Este teste usa GitHub Pages (grátis) porque é um **teste interno** da Ethos, sem verba adicional. Isso **não significa** que a Ethos vai ignorar hospedagem/domínio como parte da entrega — pelo contrário: um cliente real vai precisar de domínio próprio e hospedagem paga por ele. O procedimento completo disso (Hostinger, hPanel, apontamento de domínio, cache Hostinger+Cloudflare) já está documentado em detalhe na nota de origem da Atena e continua válido como referência operacional para quando houver entrega a cliente pagante.

## Método

1. Gerar a landing page (HTML + CSS puro, sem framework) com Claude Code, numa única passada, usando os campos estruturados do prompt do vídeo (cores + estrutura obrigatória de seções).
2. Não editar manualmente depois de gerado (mesma regra do teste anterior).
3. Versionar com git e publicar via GitHub CLI (repositório + GitHub Pages via API).
4. Verificar publicação real via HTTP.

## Resultado

| Critério | Resultado |
|---|---|
| Tempo de geração (prompt → arquivo pronto) | ~1min10s, uma passada, sem iteração |
| Retrabalho manual necessário | Nenhum |
| Estrutura de seções pedida no prompt (Hero, Benefícios, Oferta, Prova social, FAQ, CTA) | Todas presentes |
| Custo adicional | Zero |
| Publicação real (URL pública) | **Sim** — https://ethosstudioai.github.io/ethos-teste-lp-prompt-estruturado/ |
| Tempo total (arquivo gerado → site no ar, HTTP 200) | ~2min43s |
| Evidência visual (screenshot) | **Não capturada nesta rodada** — ferramentas de navegador (Chrome) não estavam disponíveis na sessão do Lex; verificação feita por status HTTP real (200). Recomendo abrir o link para conferência visual. |

## Correção pós-teste: falta de imagens (feedback de Mica, 26/07/2026)

A primeira versão gerada por Claude Code não incluiu nenhuma fotografia real — só um bloco de gradiente decorativo e emojis como ícones. Mica identificou o problema ao revisar. Correção aplicada:

- Adicionadas 5 fotos reais de banco de imagens gratuito e livre de uso comercial (Pexels, sem custo, sem necessidade de atribuição): 1 no hero, 1 na seção de oferta, 3 em uma nova seção de galeria ("como é o atendimento na prática").
- Fotos baixadas e versionadas dentro do próprio repositório (`images/`), não hotlinkadas em CDN externo — mais robusto para publicação real.
- Republicado e confirmado no ar via HTTP 200 (página e imagens).

**Aprendizado para próximos testes:** o prompt estruturado do vídeo original (Claude Design) provavelmente gera ou sugere imagens/ilustrações como parte do próprio processo de design visual — ao usar Claude Code (que só escreve código, não gera imagens), esse passo fica ausente por padrão e precisa ser adicionado manualmente como uma etapa própria do processo (buscar/inserir imagens reais), não é algo automático. Isso deve entrar como campo explícito em qualquer prompt estruturado futuro para landing pages.

## Terceira rodada: direção visual com referências reais (26-27/07/2026)

Mica apontou que gerar sem referência estava saindo genérico. Fui atrás de 4 landing pages reais de clínicas de fisioterapia bem avaliadas (via pesquisa, sem ferramenta de navegador nesta sessão — leitura de conteúdo/estrutura, não inspeção visual direta): [Finish Strong PT](https://www.finishstrongpt.com) (calor atlético, fotografia de ação), [Bespoke Treatments](https://bespoketreatments.com) (premium), [Kaizen Physical Therapy](https://kaizenseattle.com) (confiança clínica, azul/teal) e [Physioworks PT](https://www.physioworkspt.com) (verde calmo). Mica escolheu misturar Finish Strong + Kaizen.

Direção aplicada:
- **Cor:** teal profundo (confiança clínica, de Kaizen) como cor principal + terracota/coral (energia/movimento, de Finish Strong) como acento — fundo quase-branco, não creme, para não cair no clichê "creme + serifa + terracota" comum em design gerado por IA.
- **Tipografia:** Space Grotesk (títulos) + IBM Plex Sans (corpo) + IBM Plex Mono (rótulos/estatísticas) via Google Fonts (gratuito).
- **Assinatura própria:** um pequeno traço pontilhado com marcadores (uma "trilha de movimento/articulação") ao lado de cada título de seção e, de forma sutil, atrás da foto do hero — grounded no que fisioterapia realmente é (rastrear movimento e articulação), não decoração aleatória.

## Avaliação do critério de sucesso

Critério (mesmo do teste anterior, adaptado): página gerada em uma passada, sem retrabalho manual, publicada de verdade, sem custo adicional, com a estrutura de seções completa do prompt do vídeo.

- Gerada em uma passada, sem retrabalho: **atendido**.
- Publicada com URL pública real: **atendido**.
- Custo adicional: **zero**.
- Estrutura completa (Hero, Benefícios, Oferta, Prova social, FAQ, CTA): **atendido**.

**Critério de sucesso batido.** Confirma que a técnica de prompt estruturado do vídeo funciona também com a ferramenta e a hospedagem que a Ethos já validou — não é exclusiva do Claude Design + Hostinger mostrados no vídeo original.

## Limitação desta rodada

Sem verificação visual automatizada (screenshot) — a sessão do Lex não tinha acesso às ferramentas de navegador neste momento. A verificação foi por HTTP real (200, conteúdo publicado), não por inspeção visual. Se quiser confirmação visual formal, é só pedir uma nova rodada com essa ferramenta disponível, ou conferir o link diretamente.

## Arquivos

- `index.html` — a landing page gerada (na raiz, requisito do GitHub Pages).
- Repositório git local + remoto (`ethosstudioai/ethos-teste-lp-prompt-estruturado` no GitHub, publicado via GitHub Pages).

## Conexões

- [[../../02_Conhecimento/01_Estudos/youtube-descomplicandosites-landing-page-claude-design|Estudo de origem — Atena]]
- [[../Teste_Site_Claude_Code/README|Teste anterior — criar site com Claude Code]]
- [[../INDICE|Índice de Produtos e Automações]]
- [[../../00_Direcao/CONTEXTO_ATIVO|Contexto Ativo]]
