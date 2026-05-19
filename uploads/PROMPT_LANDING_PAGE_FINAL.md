# PROMPT FINAL — LANDING PAGE DR. MATEUS MARQUES
*(versão com correções SEO + mobile-first aplicadas)*

Build a complete, production-ready single-page HTML landing page in Brazilian Portuguese for Dr. Mateus Marques — Cirurgião Torácico. This is his primary digital presence: Instagram bio link, Google-indexed, running paid ads. Deliver a single `.html` file with all CSS in `<style>` and all JS in `<script>`. No external frameworks except Google Fonts.

**CRITICAL — MOBILE-FIRST ARCHITECTURE:**
The majority of visitors arrive via mobile (Instagram bio link, WhatsApp, Google mobile search). Write ALL CSS mobile-first:
- Base styles target mobile (320px–767px) — no `max-width` wrappers
- Use `min-width` media queries exclusively to progressively enhance for larger screens:
  - `@media (min-width: 768px)` → tablet
  - `@media (min-width: 1024px)` → desktop
- Every section must be fully usable on a 375px screen before touching desktop layout
- Touch targets minimum 48×48px (buttons, links, accordion triggers)
- WhatsApp CTA button must be visible without scrolling on mobile hero
- Font sizes: never below 15px for body text on mobile (legibility)
- Accordion is the preferred pattern on mobile for specialty content (already specified)
- Carousel shows 1 card at a time on mobile with swipe support
- No horizontal overflow at any mobile breakpoint (`overflow-x: hidden` on body)
- Google uses mobile-first indexing: the mobile version is what gets ranked

---

## GLOBAL VARIABLES & CONSTANTS

```
WhatsApp number: 5575981872440
Instagram: @drmateus_cirtorax
Instagram URL: https://instagram.com/drmateus_cirtorax

Default WhatsApp message (all generic CTAs):
"Olá! Vim do site e gostaria de agendar uma consulta com dr Mateus!"

WhatsApp base URL:
https://wa.me/5575981872440?text=

Waze link: https://ul.waze.com/ul?place=ChIJVY8jp445FAcROlWg4CzC76I&ll=-12.23675370%2C-38.94600360&navigate=yes&utm_campaign=default&utm_source=waze_website&utm_medium=lm_share_location
Google Maps link: https://maps.app.goo.gl/gVmY29SyXHuWuGGR9

Phone (ligações — para pacientes que preferem ligar, especialmente idosos):
+55 71 98828-7588
Phone link: tel:+5571988287588
```

---

## BRAND SYSTEM

Colors (CSS variables):

```css
--navy-deep: #0B1520;
--navy-mid: #111E2E;
--navy-card: #162030;
--silver: #A8BAC8;
--silver-light: #D0DCE6;
--gold: #C9A96E;
--gold-muted: #9B7D52;
--text-primary: #EEF2F6;
--text-muted: #7A92A3;
--text-dim: #4A6070;
--white: #FFFFFF;
```

Typography (Google Fonts):
- `Cormorant Garamond` — weights 300, 400, 500, 600i (display, headings, pull quotes)
- `DM Sans` — weights 300, 400, 500 (body, UI, labels, buttons)

Visual language: Luxury medical editorial. Generous negative space. Gold hairlines as section dividers (`1px solid #C9A96E` at 30% opacity). Subtle noise texture overlay on dark sections (SVG filter or CSS). No cheap gradients. Depth through layering, not glow.

---

## SEO & TECHNICAL *(coloque no `<head>` — ordem importante)*

```html
<meta charset="UTF-8">
<meta name="viewport" content="width=device-width, initial-scale=1.0">

<!-- SEO primário -->
<title>Dr. Mateus Marques | Cirurgião Torácico em Feira de Santana – BA</title>
<meta name="description" content="Cirurgião torácico em Feira de Santana, BA. Especialista em cirurgia minimamente invasiva (VATS): nódulos pulmonares, hiperidrose, pneumotórax, tumores torácicos e derrame pleural. Agende sua consulta.">
<meta name="robots" content="index, follow">
<link rel="canonical" href="https://www.drmateusmarques.com/">

<!-- Open Graph (WhatsApp, Instagram, redes sociais) -->
<meta property="og:type" content="website">
<meta property="og:url" content="https://www.drmateusmarques.com/">
<meta property="og:title" content="Dr. Mateus Marques | Cirurgião Torácico em Feira de Santana – BA">
<meta property="og:description" content="Especialista em cirurgia torácica minimamente invasiva. Agende sua avaliação em Feira de Santana, BA.">
<meta property="og:image" content="https://www.drmateusmarques.com/img/og-cover.jpg">
<meta property="og:locale" content="pt_BR">

<!-- Google Fonts -->
<link rel="preconnect" href="https://fonts.googleapis.com">
<link rel="preconnect" href="https://fonts.gstatic.com" crossorigin>
<link href="https://fonts.googleapis.com/css2?family=Cormorant+Garamond:ital,wght@0,300;0,400;0,500;1,600&family=DM+Sans:wght@300;400;500&display=swap" rel="stylesheet">

<!-- Schema.org — Physician completo (gera estrelas no Google) -->
<script type="application/ld+json">
{
  "@context": "https://schema.org",
  "@type": "Physician",
  "name": "Dr. Mateus Marques de Amorim",
  "medicalSpecialty": "Thoracic Surgery",
  "identifier": "CRM-BA 28632",
  "url": "https://www.drmateusmarques.com",
  "telephone": "+55-75-98187-2440",
  "address": {
    "@type": "PostalAddress",
    "streetAddress": "Av. João Durval Carneiro, 3803 – Edf. Charmant Prime, sala 15, 3º andar",
    "addressLocality": "Feira de Santana",
    "addressRegion": "BA",
    "postalCode": "44051-335",
    "addressCountry": "BR"
  },
  "geo": {
    "@type": "GeoCoordinates",
    "latitude": -12.2368,
    "longitude": -38.9460
  },
  "openingHoursSpecification": {
    "@type": "OpeningHoursSpecification",
    "dayOfWeek": ["Monday","Tuesday","Wednesday","Thursday","Friday"],
    "opens": "08:00",
    "closes": "18:00"
  },
  "aggregateRating": {
    "@type": "AggregateRating",
    "ratingValue": "5.0",
    "reviewCount": "111"
  },
  "sameAs": [
    "https://instagram.com/drmateus_cirtorax",
    "https://www.doctoralia.com.br/mateus-marques-de-amorim/cirurgiao-toracico/feira-de-santana"
  ]
}
</script>

<!-- Schema.org — FAQPage (rich snippets nas buscas) -->
<script type="application/ld+json">
{
  "@context": "https://schema.org",
  "@type": "FAQPage",
  "mainEntity": [
    {
      "@type": "Question",
      "name": "Quando devo procurar um cirurgião torácico?",
      "acceptedAnswer": {
        "@type": "Answer",
        "text": "O cirurgião torácico é o especialista em todas as doenças do tórax que podem ser tratadas com cirurgia — nódulos e massas pulmonares, câncer de pulmão, doenças da pleura, alterações no mediastino, deformidades ou lesões na parede torácica, doenças da via aérea e da traqueia, e suor excessivo (hiperidrose). Na maioria das vezes o encaminhamento vem de outro médico, mas você também pode buscar avaliação diretamente, especialmente se já tem um exame com achado suspeito."
      }
    },
    {
      "@type": "Question",
      "name": "Nódulo no pulmão tem cura? Precisa operar?",
      "acceptedAnswer": {
        "@type": "Answer",
        "text": "Nem todo nódulo pulmonar é maligno — a maioria é benigno e pode ser acompanhado sem cirurgia. A decisão de operar depende do tamanho, das características na tomografia, do histórico de tabagismo e de outros fatores de risco. Quando a cirurgia é indicada, ela pode ser feita por videotoracoscopia (VATS), com pequenas incisões, recuperação rápida e alto índice de cura quando o diagnóstico é precoce."
      }
    },
    {
      "@type": "Question",
      "name": "O que é hiperidrose e como é o tratamento?",
      "acceptedAnswer": {
        "@type": "Answer",
        "text": "Hiperidrose é a condição em que o corpo produz suor excessivo, muitas vezes não relacionado a estímulos como atividade física ou calor intenso. Uma das opções para tratamento definitivo é a simpatectomia — secção dos nervos responsáveis pelo estímulo excessivo do suor, realizada por pequenas incisões, com internamento curto e resolução na grande maioria dos pacientes."
      }
    },
    {
      "@type": "Question",
      "name": "A cirurgia para hiperidrose é segura? Tem efeitos colaterais?",
      "acceptedAnswer": {
        "@type": "Answer",
        "text": "A simpatectomia torácica videotoracoscópica é um procedimento bem estabelecido, realizado por pequenas incisões, normalmente com alta hospitalar no dia seguinte e índice de sucesso superior a 95% para hiperidrose palmar. O principal efeito colateral é a hiperidrose compensatória — suor aumentado em outras regiões do corpo — que pode acontecer em alguns pacientes."
      }
    },
    {
      "@type": "Question",
      "name": "O que é cirurgia minimamente invasiva torácica (VATS)?",
      "acceptedAnswer": {
        "@type": "Answer",
        "text": "A videotoracoscopia (VATS) é a abordagem em que o cirurgião opera através de pequenas incisões de 1 a 2 cm, usando câmera e instrumentos especiais. Ela substitui a cirurgia aberta na maioria dos casos, oferecendo menos dor, internação mais curta, retorno mais rápido às atividades e resultados equivalentes ou superiores."
      }
    },
    {
      "@type": "Question",
      "name": "Pneumotórax tem cura? Pode voltar depois da cirurgia?",
      "acceptedAnswer": {
        "@type": "Answer",
        "text": "O pneumotórax espontâneo tem tratamento eficaz. O problema é a recidiva: cerca de 30 a 50% dos pacientes têm novo episódio sem tratamento cirúrgico. A cirurgia por VATS, com ressecção das bolhas e pleurodese mecânica, reduz drasticamente o risco de recorrência e é indicada principalmente após o segundo episódio ou em pacientes de alto risco."
      }
    },
    {
      "@type": "Question",
      "name": "Derrame pleural é grave? Qual o tratamento?",
      "acceptedAnswer": {
        "@type": "Answer",
        "text": "O derrame pleural pode ser leve ou grave dependendo da causa e do volume. O tratamento varia conforme a origem: drenagem simples, cateter pleural de longa permanência ou pleurodese cirúrgica nos casos recidivantes. Identificar e tratar a causa do derrame é tão importante quanto retirar o líquido."
      }
    },
    {
      "@type": "Question",
      "name": "Qual a diferença entre cirurgião torácico e pneumologista?",
      "acceptedAnswer": {
        "@type": "Answer",
        "text": "O pneumologista é o especialista clínico das doenças do pulmão — diagnostica, acompanha e trata com medicamentos. O cirurgião torácico é o especialista cirúrgico — opera quando o tratamento exige intervenção: ressecção de tumores, tratamento do pneumotórax, drenagem de derrames complexos, cirurgia da traqueia. Em muitos casos os dois trabalham juntos."
      }
    },
    {
      "@type": "Question",
      "name": "Como é a recuperação após uma cirurgia torácica?",
      "acceptedAnswer": {
        "@type": "Answer",
        "text": "Nas cirurgias videotoracoscópicas (VATS), a internação costuma ser de 1 a 3 dias e o retorno às atividades leves ocorre em 1 a 2 semanas. Cirurgias mais complexas têm recuperação de 3 a 6 semanas. O acompanhamento pós-operatório próximo é parte essencial do tratamento."
      }
    },
    {
      "@type": "Question",
      "name": "As cirurgias são cobertas pelo convênio?",
      "acceptedAnswer": {
        "@type": "Answer",
        "text": "Sim. A maioria dos procedimentos cirúrgicos é coberta pelos principais convênios. Aceitamos Unimed, Bradesco Saúde, SulAmérica, Amil, Planserv, CASSI, GEAP, Saúde Caixa, ASFEB, Postal Saúde, FUSEX, União Médica e Petrobras, entre outros."
      }
    }
  ]
}
</script>
```

---

## SECTION 0 — FIXED HEADER

Sticky top bar. Background: `#0B1520` at 95% opacity with `backdrop-filter: blur(12px)`. Height: 68px. Thin gold hairline bottom border.

Left: Logo — Usar `<img src="img/logo-mm.png" alt="MM" height="44" style="display:block">` (logo oficial disponível: monograma MM integrado com forma de pulmão, letras silver + pulmão navy, fundo preto — usar com `mix-blend-mode: lighten` ou fundo escuro para o preto sumir). Seguido de:
- Line 1: `MATEUS MARQUES` in DM Sans 500, uppercase, letter-spacing 0.15em, silver, 13px
- Line 2: `CIRURGIÃO TORÁCICO` in DM Sans 300, uppercase, letter-spacing 0.12em, gold-muted, 10px

Center (desktop only): Smooth-scroll anchor nav links in DM Sans 400, 13px, text-muted, uppercase, letter-spacing 0.1em. Hover: text turns silver-light. Links:
- `Sobre` → `#sobre`
- `Especialidades` → `#especialidades`
- `Avaliações` → `#avaliacoes`
- `Perguntas Frequentes` → `#faq`
- `Convênios` → `#convenios`
- `Localização` → `#localizacao`
- `Contato` → `#contato`

Right: Two items:
1. Instagram icon link → `https://instagram.com/drmateus_cirtorax` — opens new tab, icon in silver, hover turns gold
2. Button `"Agendar Consulta"` — DM Sans 500, 12px, uppercase, letter-spacing 0.08em. Style: thin silver border, transparent fill, silver text. Hover: silver fill, navy text, transition 200ms. Links to WhatsApp default message.

Mobile: Hamburger menu (3 gold lines). Opens full-screen overlay nav with all links + CTA. Logo left, hamburger right.

---

## SECTION 1 — HERO

Full viewport height (`100dvh`). Background `#0B1520` + subtle SVG noise texture overlay (5% opacity).

Layout mobile (base): coluna única. Ordem: label → headline → subheadline → CTA primário → foto (abaixo, full-width, aspect-ratio 4/5, sem fade lateral) → stats strip. O botão "Agendar Consulta" deve estar visível sem scroll em qualquer celular ≥ 375px.
Layout desktop (`min-width: 1024px`): Asymmetric two-column. Left 55% text, right 45% photo.

Photo treatment: Usar `<img src="img/foto-dr-mateus.jpg" alt="Dr. Mateus Marques">` (foto oficial disponível: retrato profissional, terno azul, fundo cinza neutro, mãos entrelaçadas). Apply CSS: `object-fit: cover; object-position: top center`, height 85% viewport, slight desaturation filter (`filter: saturate(0.85)`). Left edge fades into background via CSS mask (`mask-image: linear-gradient(to right, transparent 0%, black 30%)`). No border, no card — just the figure emerging from darkness.

Left column content (vertically centered, padding-left 8vw):

Label above headline (DM Sans 300, 11px, gold, uppercase, letter-spacing 0.2em):
`CIRURGIA TORÁCICA MINIMAMENTE INVASIVA`

Headline (Cormorant Garamond 300, ~76px, line-height 1.1, text-primary):
"Quando o diagnóstico é sério, o cirurgião importa."

Subheadline (DM Sans 300, 18px, text-muted, max-width 440px, line-height 1.75, margin-top 28px):
"Especialista em cirurgia torácica minimamente invasiva. Atendimento com clareza, técnica e presença — do diagnóstico à recuperação."

Primary CTA (margin-top 44px): Button `"Agendar Consulta"` — DM Sans 500, 14px, uppercase, letter-spacing 0.1em. Padding 16px 36px. Border: `1px solid #A8BAC8`. Background transparent. Color silver. Hover: background `#A8BAC8`, color `#0B1520`, transform scale(1.02). Transition 250ms ease. WhatsApp default message link.

Secondary link (margin-top 16px):
"Atendimento presencial e teleconsulta disponíveis →" DM Sans 300, 14px, text-muted. Hover: silver-light. Smooth scrolls to `#contato`.

Trust strip (absolute bottom of hero, full width, centered): Thin gold line top. Padding 18px. DM Sans 300, 10px, letter-spacing 0.18em, uppercase, text-dim:
`TÍTULO DE ESPECIALISTA EM CIRURGIA TORÁCICA PELA SBCT · ATUA NOS MELHORES HOSPITAIS DE FEIRA DE SANTANA · ESPECIALISTA EM PROCEDIMENTOS MINIMAMENTE INVASIVOS · ALTÍSSIMA TAXA DE SATISFAÇÃO COM ABORDAGEM HUMANIZADA`

Load animations (staggered CSS keyframes):
- Label: fade+slideUp, delay 0.2s
- Headline: fade+slideUp, delay 0.5s
- Subheadline: fade+slideUp, delay 0.8s
- CTA: fade+slideUp, delay 1.0s
- Photo: fadeIn from right (translateX 30px → 0), delay 0.6s, duration 1.2s

---

## SECTION 2 — SOBRE MIM (`id="sobre"`)

Background: `#111E2E`. Gold hairline top. Padding: 120px 8vw.

Layout desktop: Two columns, gap 80px.

Left column:

Small label (DM Sans 300, 11px, gold uppercase, letter-spacing 0.2em):
`SOBRE O MÉDICO`

Pull quote (Cormorant Garamond 400 italic, 38px, silver-light, line-height 1.35, margin-top 20px):
"Cada paciente merece um cirurgião que realmente compreenda o que está em jogo."

Gold hairline divider (width 60px, height 1px, margin 32px 0).

Credential pills (DM Sans 300, 12px, text-muted) — each with a small gold dot `·` before:
`· Residência em Cirurgia Torácica` `· Cirurgia Minimamente Invasiva (VATS)` `· Fellowships Internacionais` `· Membro da SBCT` `· Atendimento presencial e teleconsulta`

Right column:

Body text (DM Sans 300, 16px, text-muted, line-height 1.85):
"Sou Mateus Marques, cirurgião torácico dedicado ao tratamento cirúrgico das doenças do tórax com a menor invasão possível — porque menos trauma significa recuperação mais rápida, menos dor e melhores resultados.

Minha formação foi construída em centros de referência e complementada com experiências internacionais. Mas o que mais me guia no dia a dia é algo mais simples: a escuta.

Antes de qualquer decisão cirúrgica, preciso entender o paciente — seus medos, sua rotina, o que essa doença representa na sua vida. Só assim consigo oferecer o que cada caso realmente precisa.

Atendo pacientes com doenças do pulmão, pleura, mediastino, parede torácica e traqueia, em situações eletivas e de maior complexidade. Se você chegou aqui com um diagnóstico na mão e mais perguntas do que respostas, esse é exatamente o lugar certo."

CTA link (margin-top 36px):
Button `"Agendar Consulta"` — same style as hero primary. WhatsApp default message.

Scroll-in animation: Both columns fade+slideUp on Intersection Observer trigger.

---

## SECTION 3 — INTERSTITIAL CTA BAND

Background: `#0D1C2C`. Gold hairlines top and bottom. Padding 80px 8vw. Centered.

Headline (Cormorant Garamond 300, 42px, text-primary):
"Recebeu um diagnóstico e ainda tem dúvidas?"

Subtext (DM Sans 300, 16px, text-muted, margin-top 16px, max-width 520px, margin-inline auto):
"Nossa equipe está disponível para orientar, esclarecer e agendar — sem burocracia e com agilidade."

Button (margin-top 36px): `"Agendar Consulta"` — gold border `#C9A96E`, transparent fill, gold text. Hover: gold fill, navy text. WhatsApp default message.

---

## SECTION 4 — ÁREAS DE ATUAÇÃO (`id="especialidades"`)

Background: `#0B1520`. Gold hairline top. Padding: 120px 8vw.

Header:
- Label (DM Sans 300, 11px, gold uppercase, letter-spacing 0.2em): `ESPECIALIDADES`
- Title (Cormorant Garamond 300, 54px, text-primary, margin-top 12px): "O que eu trato"
- Subtext (DM Sans 300, 16px, text-muted, margin-top 16px): "Selecione uma área para entender como posso ajudar no seu caso."

Accordion — max-width 860px, margin-inline auto, margin-top 64px.

Each item:
- Collapsed: full-width row. Left: area name (DM Sans 500, 17px, silver-light). Right: `+` icon (gold, 20px, rotates 45° on open, transition 300ms).
- Thin gold hairline `1px solid rgba(201,169,110,0.2)` below each item.
- Active item: left border `3px solid #C9A96E`, background `#162030`, name color `#D0DCE6`.
- Expanded content: `max-height` transition from 0 → auto (JS sets explicit px height), `overflow hidden`, `transition: max-height 350ms ease`.
- Expanded inner: padding 24px 0 32px. Body text DM Sans 300, 15px, text-muted, line-height 1.8. Then inline CTA link.
- **Each accordion item uses `aria-expanded` no botão e `id` + `aria-controls` no painel — obrigatório para acessibilidade e SEO.**

### CADA ACCORDION — copy completo + mensagem WhatsApp:

**① Hiperidrose**
Body: "A hiperidrose é o suor excessivo — nas mãos, axilas ou pés — que vai além do controle e interfere diretamente na vida social e profissional. O impacto é real: apertos de mão evitados, roupas molhadas, insegurança constante.
O tratamento cirúrgico, a simpatectomia torácica videotoracoscópica, é realizado por pequenas incisões com anestesia geral, alta em 24 horas e resolução definitiva na grande maioria dos pacientes. Se você já tentou antitranspirantes, botox ou outros recursos sem resultado, a cirurgia pode ser a solução."
CTA: `"Quero saber se sou candidato(a) →"` WA: `"Olá! Vim do site e gostaria de agendar uma consulta com dr Mateus para avaliar Hiperidrose!"`

**② Nódulo / Massa Pulmonar**
Body: "Um nódulo ou massa pulmonar descoberto em uma tomografia gera ansiedade imediata — e exige avaliação especializada com urgência. Nem todo nódulo é maligno, mas todo nódulo precisa de um olhar experiente para definir risco, indicar biópsias quando necessário e, se preciso, realizar a ressecção com técnica minimamente invasiva.
Cuido de toda a jornada: da investigação ao diagnóstico, do planejamento à cirurgia — com comunicação clara em cada etapa."
CTA: `"Tenho um nódulo — o que fazer? →"` WA: `"Olá! Vim do site e gostaria de agendar uma consulta com dr Mateus para avaliar Nódulo Pulmonar!"`

**③ Tumores de Parede Torácica**
Body: "Os tumores que acometem costelas, esterno ou tecidos moles da caixa torácica exigem planejamento cirúrgico criterioso — para garantir a ressecção completa e a reconstrução adequada da parede torácica.
Com técnica adequada, é possível remover o tumor com margem segura e restaurar tanto a estabilidade quanto a função respiratória, preservando qualidade de vida no pós-operatório."
CTA: `"Agendar avaliação →"` WA: `"Olá! Vim do site e gostaria de agendar uma consulta com dr Mateus para avaliar Tumor de Parede Torácica!"`

**④ Tumores de Pleura**
Body: "A pleura é a membrana que envolve o pulmão. Quando afetada por tumores — como o mesotelioma — o tratamento exige abordagem especializada e frequentemente multimodal.
Realizo pleurectomia e procedimentos videoassistidos com foco no controle da doença, no alívio de sintomas como a falta de ar e na preservação da qualidade de vida durante todo o tratamento."
CTA: `"Falar sobre o meu caso →"` WA: `"Olá! Vim do site e gostaria de agendar uma consulta com dr Mateus para avaliar Tumor de Pleura!"`

**⑤ Tumores de Mediastino**
Body: "O mediastino é o espaço central do tórax — abriga coração, grandes vasos, esôfago e estruturas vitais. Timomas, cistos, linfomas e outras massas mediastinais têm apresentações variadas e exigem diagnóstico preciso antes de qualquer decisão.
A ressecção videoassistida (VATS) permite abordar essas lesões com menor morbidade, menos dor e recuperação mais rápida do que a cirurgia convencional aberta."
CTA: `"Quero uma avaliação especializada →"` WA: `"Olá! Vim do site e gostaria de agendar uma consulta com dr Mateus para avaliar Tumor de Mediastino!"`

**⑥ Derrame Pleural**
Body: "O derrame pleural — acúmulo de líquido ao redor do pulmão — causa falta de ar progressiva e pode ter diversas origens: infecção, câncer, insuficiência cardíaca ou doenças sistêmicas.
O tratamento varia da drenagem simples ao cateter pleural de longa permanência ou pleurodese cirúrgica. A escolha depende da causa e do contexto clínico — sempre com o objetivo de aliviar os sintomas e tratar o problema de base."
CTA: `"Entender meu tratamento →"` WA: `"Olá! Vim do site e gostaria de agendar uma consulta com dr Mateus para avaliar Derrame Pleural!"`

**⑦ Pneumotórax**
Body: "O pneumotórax — acúmulo de ar entre o pulmão e a parede do tórax — pode ocorrer espontaneamente (especialmente em jovens altos e magros) ou após trauma. O primeiro episódio pode ser tratado de forma conservadora, mas a recidiva muda a equação.
Nos casos recidivantes ou de alto risco, a cirurgia videoassistida (VATS) é a abordagem mais eficaz: pequenas incisões, alta precoce e prevenção definitiva de novos episódios."
CTA: `"Meu pneumotórax voltou — e agora? →"` WA: `"Olá! Vim do site e gostaria de agendar uma consulta com dr Mateus para avaliar Pneumotórax!"`

**⑧ Traqueia**
Body: "As doenças da traqueia — como a estenose (estreitamento) após intubação prolongada ou traqueostomia — comprometem gravemente a respiração e exigem manejo altamente especializado.
A ressecção e reconstrução traqueal é um dos procedimentos mais complexos e delicados da cirurgia torácica. Ofereço avaliação completa e, quando indicado, abordagem cirúrgica com foco em resultado duradouro e preservação da voz e da função respiratória."
CTA: `"Agendar avaliação de traqueia →"` WA: `"Olá! Vim do site e gostaria de agendar uma consulta com dr Mateus para avaliar Traqueia!"`

---

## SECTION 4B — PERGUNTAS FREQUENTES (`id="faq"`)

> ⚠️ NOTA TÉCNICA — @type e medicalSpecialty em inglês: Os valores `"Physician"` e `"Thoracic Surgery"` no JSON-LD devem permanecer em inglês. Schema.org é um padrão internacional e exige os nomes dos tipos em inglês, independentemente do idioma da página. Os campos de conteúdo (endereço, descrições, perguntas, respostas) continuam corretamente em português.

Background: `#0B1520`. Gold hairline top. Padding 100px 8vw.

Header:
- Label (DM Sans 300, 11px, gold uppercase, letter-spacing 0.2em): `DÚVIDAS FREQUENTES`
- Title (Cormorant Garamond 300, 48px, text-primary): "Perguntas frequentes"
- Subtext (DM Sans 300, 15px, text-muted, margin-top 12px): "Tire suas dúvidas sobre cirurgia torácica, procedimentos e atendimento."

Layout: Single column, max-width 780px, centered. Margin-top 56px.

Accordion component (vanilla JS). Each item:
- Border-bottom: `1px solid rgba(168,186,200,0.1)`
- Question row: padding 24px 0. DM Sans 500, 16px, silver-light. Cursor pointer. Chevron icon (gold, 16px) right-aligned — rotates 180° when open. Hover: gold color on text.
- Answer panel: hidden by default. Expands with smooth CSS max-height transition (300ms ease). DM Sans 300, 15px, text-muted, line-height 1.85. Padding-bottom 24px.
- Todos os itens fechados por default.

**10 perguntas e respostas:**

**① Quando devo procurar um cirurgião torácico?**
"O cirurgião torácico é o especialista em todas as doenças do tórax que podem ser tratadas com cirurgia — nódulos e massas pulmonares, câncer de pulmão, doenças da pleura, alterações no mediastino, deformidades ou lesões na parede torácica, doenças da via aérea e da traqueia, e suor excessivo (hiperidrose). Na maioria das vezes o encaminhamento vem de outro médico, mas você também pode buscar avaliação diretamente, especialmente se já tem um exame com achado suspeito."

**② Nódulo no pulmão tem cura? Precisa operar?**
"Nem todo nódulo pulmonar é maligno — a maioria é benigno e pode ser acompanhado sem cirurgia. A decisão de operar depende do tamanho, das características na tomografia, do histórico de tabagismo e de outros fatores de risco. Quando a cirurgia é indicada, ela pode ser feita por videotoracoscopia (VATS), com pequenas incisões, recuperação rápida e alto índice de cura quando o diagnóstico é precoce."

**③ O que é hiperidrose e como é o tratamento?**
"Hiperidrose é a condição em que o corpo produz suor excessivo, muitas vezes não relacionado a estímulos como atividade física ou calor intenso. Uma das opções para tratamento definitivo é a simpatectomia — secção dos nervos responsáveis pelo estímulo excessivo do suor, realizada por pequenas incisões, com internamento curto e resolução na grande maioria dos pacientes."

**④ A cirurgia para hiperidrose é segura? Tem efeitos colaterais?**
"A simpatectomia torácica videotoracoscópica é um procedimento bem estabelecido, realizado por pequenas incisões, normalmente com alta hospitalar no dia seguinte e índice de sucesso superior a 95% para hiperidrose palmar. O principal efeito colateral é a hiperidrose compensatória — suor aumentado em outras regiões do corpo — que pode acontecer em alguns pacientes."

**⑤ O que é cirurgia minimamente invasiva torácica (VATS)?**
"A videotoracoscopia (VATS) é a abordagem em que o cirurgião opera através de pequenas incisões de 1 a 2 cm, usando câmera e instrumentos especiais. Ela substitui a cirurgia aberta na maioria dos casos, oferecendo menos dor, internação mais curta, retorno mais rápido às atividades e resultados equivalentes ou superiores."

**⑥ Pneumotórax tem cura? Pode voltar depois da cirurgia?**
"O pneumotórax espontâneo tem tratamento eficaz. O problema é a recidiva: cerca de 30 a 50% dos pacientes têm novo episódio sem tratamento cirúrgico. A cirurgia por VATS, com ressecção das bolhas e pleurodese mecânica, reduz drasticamente o risco de recorrência e é indicada principalmente após o segundo episódio ou em pacientes de alto risco."

**⑦ Derrame pleural é grave? Qual o tratamento?**
"O derrame pleural pode ser leve ou grave dependendo da causa e do volume. O tratamento varia conforme a origem: drenagem simples, cateter pleural de longa permanência ou pleurodese cirúrgica nos casos recidivantes. Identificar e tratar a causa do derrame é tão importante quanto retirar o líquido."

**⑧ Qual a diferença entre cirurgião torácico e pneumologista?**
"O pneumologista é o especialista clínico das doenças do pulmão — diagnostica, acompanha e trata com medicamentos. O cirurgião torácico é o especialista cirúrgico — opera quando o tratamento exige intervenção: ressecção de tumores, tratamento do pneumotórax, drenagem de derrames complexos, cirurgia da traqueia. Em muitos casos os dois trabalham juntos."

**⑨ Como é a recuperação após uma cirurgia torácica?**
"Nas cirurgias videotoracoscópicas (VATS), a internação costuma ser de 1 a 3 dias e o retorno às atividades leves ocorre em 1 a 2 semanas. Cirurgias mais complexas têm recuperação de 3 a 6 semanas. O acompanhamento pós-operatório próximo é parte essencial do tratamento."

**⑩ As cirurgias são cobertas pelo convênio?**
"Sim. A maioria dos procedimentos cirúrgicos é coberta pelos principais convênios. Aceitamos Unimed, Bradesco Saúde, SulAmérica, Amil, Planserv, CASSI, GEAP, Saúde Caixa, ASFEB, Postal Saúde, FUSEX, União Médica e Petrobras, entre outros."

Add FAQ section link to navigation: `"FAQ"` → `#faq`

---

## SECTION 5 — CONVÊNIOS ACEITOS (`id="convenios"`)

Background: `#111E2E`. Gold hairline top. Padding 100px 8vw.

Header:
- Label (DM Sans 300, 11px, gold uppercase, letter-spacing 0.2em): `CONVÊNIOS`
- Title (Cormorant Garamond 300, 48px, text-primary): "Planos aceitos"
- Subtext (DM Sans 300, 15px, text-muted, margin-top 12px): "Atendimento também particular. Entre em contato para verificar cobertura do seu plano."

Grid layout: Responsive grid — 5 columns desktop, 3 tablet, 2 mobile. Gap 24px. Margin-top 56px.

Each card:
- Background: `#162030`
- Border: `1px solid rgba(168,186,200,0.1)`
- Border-radius: 8px
- Padding: 28px 20px
- Centered content
- Hover: border-color `rgba(201,169,110,0.4)`, transform translateY(-2px), transition 250ms
- Cada card tem área de logo centralizada: container interno `background: rgba(255,255,255,0.92)`, border-radius 4px, padding 12px 16px, display flex, align-items center, justify-content center, height 52px.
- Dentro: `<img src="img/convenios/NOME.png" alt="NOME" loading="lazy" style="max-width:96px;max-height:36px;object-fit:contain">` (logos coloridos originais, fundo branco do container garante contraste)
- Hover no card: container interno border `1px solid rgba(201,169,110,0.5)`, não o logo

**Arquivos disponíveis em `img/convenios/` — usar exatamente esses nomes (todos os 13):**
- `unimed.png`
- `bradesco-saude.png`
- `sulamerica.png`
- `amil.png`
- `planserv.png`
- `cassi.png`
- `geap.png`
- `saude-caixa.png`
- `asfeb.png`
- `postal-saude.png`
- `fusex.png`
- `uniao-medica.png`
- `petrobras.png`

**Convênios a exibir (lista correta — 13 planos):**
Unimed · Bradesco Saúde · SulAmérica · Amil · Planserv · CASSI · GEAP · Saúde Caixa · ASFEB · Postal Saúde · FUSEX · União Médica · Petrobras

Below grid, centered small text (DM Sans 300, 13px, text-muted, margin-top 40px):
"Não encontrou seu plano? Entre em contato — verificamos a cobertura para você."

CTA button: `"Verificar meu plano"` → WA: `"Olá! Vim do site e gostaria de verificar se meu convênio é aceito pelo dr Mateus!"`

---

## SECTION 6 — AVALIAÇÕES (`id="avaliacoes"`)

Background: `#0B1520`. Gold hairline top. Padding 100px 8vw.

Header:
- Label: `O QUE DIZEM OS PACIENTES`
- Title (Cormorant Garamond 300, 48px): "Experiências reais"
- Subtext (DM Sans 300, 15px, text-muted): "Avaliações verificadas do Google Meu Negócio."

Google Rating summary bar (centered, margin-top 48px):
- Large number: `5.0` em Cormorant Garamond 600, 72px, gold *(nota correta: 5.0, não 4.9)*
- Row of 5 star icons (gold SVG stars, filled)
- DM Sans 300, 13px, text-muted: `Baseado em 111 avaliações no Google`
- Small Google "G" logo + text `"Ver todas no Google"`

Carousel widget (vanilla JS):
- Shows 3 cards on desktop, 1 on mobile
- Auto-advances every 5s, pauses on hover
- Navigation: left/right arrow buttons (gold, minimal SVG arrows)
- Dot indicators below (gold active, muted inactive)
- Drag/swipe on mobile

Each review card:
- Background: `#162030`
- Border: `1px solid rgba(168,186,200,0.08)`
- Border-radius: 10px
- Padding: 36px 32px
- Top row: Google avatar circle (first letter of name, random muted color bg) + name (DM Sans 500, 14px, silver-light) + `"Google"` label + date (DM Sans 300, 12px, text-dim)
- 5 gold stars row
- Review text (DM Sans 300, 15px, text-muted, line-height 1.75, margin-top 16px, max 4 lines then `…`)

**Integração Google Places API (avaliações reais):**

Buscar avaliações reais via Google Places JavaScript API. Implementar assim:

```javascript
// Configuração — preencher antes de usar:
const GOOGLE_PLACE_ID = 'COLE_AQUI_O_PLACE_ID'; // Place ID do Google Meu Negócio do Dr. Mateus
const GOOGLE_MAPS_API_KEY = 'COLE_AQUI_A_API_KEY'; // Google Maps JavaScript API key (restringir ao domínio)

// No <head>, carregar a API:
// <script src="https://maps.googleapis.com/maps/api/js?key=API_KEY&libraries=places&callback=initGoogleReviews" async defer></script>

function initGoogleReviews() {
  const service = new google.maps.places.PlacesService(document.createElement('div'));
  service.getDetails({
    placeId: GOOGLE_PLACE_ID,
    fields: ['reviews', 'rating', 'user_ratings_total']
  }, (place, status) => {
    if (status === google.maps.places.PlacesServiceStatus.OK && place.reviews) {
      // Filtrar apenas 5 estrelas, ordenar por mais recente, pegar os 8 melhores
      const reviews = place.reviews
        .filter(r => r.rating === 5)
        .slice(0, 8);
      renderReviews(reviews);
      // Atualizar o rating summary com dados reais:
      document.getElementById('google-rating').textContent = place.rating.toFixed(1);
      document.getElementById('google-count').textContent = `Baseado em ${place.user_ratings_total} avaliações no Google`;
    } else {
      // Fallback: exibir avaliações estáticas abaixo
      renderFallbackReviews();
    }
  });
}
```

Fallback (exibir se API não carregar ou Place ID não configurado):
- Ana Carla M. — "O dr Mateus foi extremamente atencioso e claro em tudo. Estava com muito medo antes da cirurgia e ele tirou cada dúvida com paciência. A cirurgia foi minimamente invasiva e me recuperei muito mais rápido do que imaginava. Recomendo sem hesitar."
- Roberto F. — "Fui encaminhado com um nódulo no pulmão e estava apavorado. O dr Mateus me recebeu com calma, explicou tudo detalhadamente e me deu segurança desde a primeira consulta. Resultado excelente. Profissional diferenciado."
- Juliana S. — "Sofri de hiperidrose por anos e nunca tinha tido coragem de procurar ajuda. Depois da cirurgia com o dr Mateus, minha vida mudou completamente. Atendimento humanizado, estrutura ótima e resultado além do que esperava."
- Marcos A. — "Segunda opinião que salvou meu tratamento. O dr Mateus foi honesto, transparente e tomou o tempo necessário para me explicar todas as opções. Cirurgia feita com sucesso. Profissional excepcional."
- Fernanda L. — "Tive pneumotórax recidivante e o dr Mateus indicou a cirurgia no momento certo. Procedimento realizado por VATS, recuperação rápida, sem complicações. Equipe toda muito atenciosa."

Cada card de avaliação: exibir avatar com inicial do nome (cor gerada por hash do nome — tom muted), nome, data formatada em pt-BR (`há X dias/meses`), 5 estrelas gold, texto da avaliação.

---

## SECTION 7 — PERGUNTAS FREQUENTES (`id="faq"`)

Background: `#111E2E`. Gold hairline top. Padding 100px 8vw.

Header:
- Label (DM Sans 300, 11px, gold uppercase, letter-spacing 0.2em): `PERGUNTAS FREQUENTES`
- Title (Cormorant Garamond 300, 48px, text-primary): "Tire suas dúvidas"
- Subtext (DM Sans 300, 15px, text-muted, margin-top 12px): "As perguntas mais comuns de quem chega até nós."

Accordion — max-width 780px, margin-inline auto, margin-top 56px. Mesmo estilo do accordion de especialidades (aria-expanded, max-height transition, gold left border ativo).

**Perguntas e respostas:**

**① Quando devo consultar um cirurgião torácico?**
"Você deve consultar um cirurgião torácico se tiver tosse persistente por mais de 3 semanas, falta de ar progressiva, nódulo pulmonar identificado em exame de imagem, suor excessivo (hiperidrose), sangue na tosse ou histórico de tabagismo."

**② O que é hiperidrose e como é tratada cirurgicamente?**
"Hiperidrose é o suor excessivo nas mãos, axilas ou pés. O tratamento cirúrgico definitivo é a simpatectomia torácica videoassistida (VATS), realizada por pequenas incisões, com alta em 24 horas e resolução na grande maioria dos pacientes."

**③ O que fazer ao descobrir um nódulo pulmonar?**
"Todo nódulo pulmonar precisa de avaliação especializada. Nem todo nódulo é maligno, mas o risco deve ser determinado por um cirurgião torácico, que definirá se é necessário acompanhamento, biópsia ou ressecção cirúrgica minimamente invasiva."

**④ As cirurgias são cobertas pelo convênio?**
"Sim. A maioria dos procedimentos cirúrgicos é coberta pelos principais convênios. Aceitamos Unimed, Bradesco Saúde, SulAmérica, Amil, Planserv, CASSI, GEAP, Saúde Caixa, ASFEB, Postal Saúde, FUSEX, União Médica e Petrobras, entre outros."

**⑤ O que é cirurgia torácica minimamente invasiva (VATS)?**
"VATS (cirurgia torácica videoassistida) é uma técnica que substitui a abertura convencional do tórax por pequenas incisões e uma câmera. O resultado é menos dor, menor tempo de internação e recuperação mais rápida."

**⑥ Qual a diferença entre cirurgião torácico e pneumologista?**
"O pneumologista é o especialista clínico das doenças do pulmão — diagnostica, acompanha e trata com medicamentos. O cirurgião torácico é o especialista cirúrgico — opera quando o tratamento exige intervenção. Em muitos casos os dois trabalham juntos."

**⑦ Como é a recuperação após uma cirurgia torácica?**
"Nas cirurgias videotoracoscópicas (VATS), a internação costuma ser de 1 a 3 dias e o retorno às atividades leves ocorre em 1 a 2 semanas. Cirurgias mais complexas têm recuperação de 3 a 6 semanas. O acompanhamento pós-operatório próximo é parte essencial do tratamento."

**⑧ Como funciona a primeira consulta?**
"Na primeira consulta é realizada uma avaliação clínica detalhada com análise dos exames prévios. A indicação cirúrgica ocorre apenas quando há critério técnico, após avaliação individualizada dos riscos, benefícios e expectativas do paciente."

CTA abaixo do accordion (centralizado, margin-top 48px): Button `"Ainda tem dúvidas? Fale conosco"` → WhatsApp default message. Estilo: gold border, transparent fill, gold text. Hover: gold fill, navy text.

---

## SECTION 8 — LOCAL DE ATENDIMENTO (`id="localizacao"`)

Background: `#111E2E`. Gold hairline top. Padding 100px 8vw.

Header:
- Label: `ONDE NOS ENCONTRAR`
- Title (Cormorant Garamond 300, 48px): "Local de atendimento"

Layout desktop: Two columns. Left 45% info + navigation buttons. Right 55% photo mosaic.

Left column:

Clinic name (DM Sans 500, 18px, silver-light, margin-top 40px): `Aura – Medicina Especializada`

Building (DM Sans 300, 14px, text-muted, margin-top 4px): `Edf. Charmant Prime`

Address (DM Sans 300, 15px, text-muted, line-height 1.75, margin-top 12px):
`Av. João Durval Carneiro, 3803 — Sala 15, 3º andar`
`Feira de Santana — BA`
`CEP: 44051-335`

Gold hairline divider (margin 28px 0).

Hours — Label (DM Sans 500, 11px, gold uppercase letter-spacing): `HORÁRIO DE ATENDIMENTO`
Segunda a Sexta: 8h às 18h

Gold hairline (margin 28px 0).

Contact options (below hours, before navigation buttons):
- Phone link for calls — importante para pacientes idosos que preferem ligar a usar WhatsApp:
  Icon: phone SVG (silver). Text: `(71) 98828-7588`. Link: `tel:+5571988287588`
  DM Sans 300, 14px, text-muted. Hover: silver-light.
- WhatsApp link: Icon: WhatsApp SVG (gold). Text: `(75) 98187-2440`. Link: WhatsApp default message.
  DM Sans 300, 14px, text-muted. Hover: silver-light.

Gold hairline (margin 28px 0).

Navigation buttons:
- `"Abrir no Waze"` → Waze brand blue, SVG icon, links to: https://ul.waze.com/ul?place=ChIJVY8jp445FAcROlWg4CzC76I&ll=-12.23675370%2C-38.94600360&navigate=yes&utm_campaign=default&utm_source=waze_website&utm_medium=lm_share_location
- `"Google Maps"` → Google Maps red, SVG pin icon, links to: https://maps.app.goo.gl/gVmY29SyXHuWuGGR9

Both: DM Sans 500, 13px, uppercase, letter-spacing 0.08em. Padding 14px 24px. Border-radius 4px.

Right column — photo mosaic: CSS grid, 2 columns, 3 rows asymmetric. `<!-- SUBSTITUIR pelas fotos reais da clínica -->` Placeholders: Fachada, Recepção, Consultório, Sala de procedimentos, Corredor. On hover: scale 1.03, overflow hidden, transition 400ms.

---

## SECTION 9 — FORMULÁRIO DE CONTATO (`id="contato"`)

Background: `#0B1520`. Gold hairline top. Padding 120px 8vw.

Header:
- Label: `FALE CONOSCO`
- Title (Cormorant Garamond 300, 52px): "Pronto para dar o próximo passo?"
- Subtext (DM Sans 300, 16px, text-muted, max-width 500px): "Preencha o formulário abaixo. Nossa equipe responderá com agilidade pelo WhatsApp."

Form (max-width 600px, margin-inline auto, margin-top 56px). `novalidate` no form element.

All fields: background transparent, border `1px solid rgba(168,186,200,0.2)`, border-radius 4px, padding 16px 20px, color text-primary, DM Sans 300 15px, placeholder text-dim. Focus: border-color `#C9A96E`, box-shadow `0 0 0 2px rgba(201,169,110,0.15)`.

Field 1 — Nome: label `NOME COMPLETO`, placeholder `Seu nome`
Field 2 — WhatsApp: label `WHATSAPP`, type="tel", placeholder `(00) 00000-0000`, JS mask `(XX) XXXXX-XXXX`
Field 3 — Motivo: label `MOTIVO DO CONTATO`, select com options:
- `Selecione o motivo…` (disabled, default)
- Agendar consulta · Segunda opinião · Nódulo / Massa Pulmonar · Hiperidrose · Pneumotórax · Derrame Pleural · Tumor de Parede Torácica · Tumor de Pleura · Tumor de Mediastino · Traqueia · Verificar convênio · Outro assunto

Submit button (full width, margin-top 36px): `"Enviar pelo WhatsApp"` — DM Sans 500, 14px, uppercase, letter-spacing 0.1em. Padding 18px. Background `#C9A96E`. Color `#0B1520`. Hover: background `#B8944A`. Scale 1.01.

WhatsApp redirect JS:
```javascript
// On form submit (prevent default):
const nome = nome_field.value.trim();
const whats = whats_field.value.trim();
const motivo = motivo_select.value;

const msg = `Olá! Vim do site e gostaria de ${motivo === 'Agendar consulta' ? 'agendar uma consulta' : 'falar sobre ' + motivo} com dr Mateus! Meu nome é ${nome} e meu WhatsApp é ${whats}.`;

window.open(`https://wa.me/5575981872440?text=${encodeURIComponent(msg)}`, '_blank');
```

Validation: campos obrigatórios. Vazio → border `rgba(220,80,80,0.6)` + shake animation 300ms.

Micro text: "Suas informações são confidenciais e utilizadas apenas para fins de agendamento."

---

## SECTION 10 — FOOTER

Background: `#060E18`. Gold hairline top. Padding 60px 8vw 40px.

Three columns desktop, stacked mobile.

Left: Logo (MM monogram + name + specialty). Below: DM Sans 300, 12px, text-dim:
`CRM-BA 28632 · Cirurgião Torácico`

Center: Nav links (DM Sans 300, 13px, text-muted, hover silver-light, vertical, gap 10px):
Sobre · Especialidades · Avaliações · Perguntas Frequentes · Convênios · Localização · Contato

Right: Social + contact:
- Instagram icon + `@drmateus_cirtorax` → Instagram link, new tab
- WhatsApp icon + `(75) 98187-2440` → WhatsApp default message link
- Phone icon + `(71) 98828-7588` → `tel:+5571988287588` (para ligações — pacientes idosos)

Bottom strip (DM Sans 300, 11px, text-dim, flex space-between):
- `© 2025 Dr. Mateus Marques. Todos os direitos reservados.`
- `Este site é informativo e não substitui consulta médica.`

---

## PERFORMANCE & ACESSIBILIDADE

- Single `.html` file, todo CSS em `<style>`, todo JS em `<script>` antes de `</body>`
- Google Fonts com `display=swap` e `preconnect`
- `loading="lazy"` em todas as imagens abaixo do fold
- `scroll-behavior: smooth` no `html`
- Todos os elementos interativos com `aria-label`
- Botões do accordion com `aria-expanded`
- Campos do formulário com `<label>` associado via `for`/`id`
- Contraste de cor ≥ 4.5:1 em todo o site

**Breakpoints (mobile-first — usar apenas `min-width`):**
```css
/* Base: mobile 320px–767px — escrever aqui o CSS padrão */

@media (min-width: 768px) {
  /* tablet: 2 colunas onde faz sentido, carousel 2 cards */
}

@media (min-width: 1024px) {
  /* desktop: layout completo, nav central visível, hero assimétrico */
}
```

**Core Web Vitals — metas para ranqueamento mobile:**
- LCP (Largest Contentful Paint) < 2.5s → hero text deve renderizar antes da foto
- CLS (Cumulative Layout Shift) < 0.1 → reservar espaço para imagens com `aspect-ratio`
- INP (Interaction to Next Paint) < 200ms → JS do accordion e carousel deve ser leve

**Layout mobile obrigatório por seção:**
- Header: logo esquerda + hamburger direita, sem nav central
- Hero: coluna única, foto abaixo do texto, CTA WhatsApp visível sem scroll
- Sobre: coluna única, foto primeiro, texto depois
- Especialidades: accordion full-width, 1 coluna
- Convênios: grid 2 colunas
- Avaliações: carousel 1 card, swipe habilitado
- Localização: coluna única, mapa/botões antes das fotos
- Contato: formulário full-width, botão WhatsApp destaque total
- Footer: stack vertical, links centralizados

---

## MOOD FINAL

Um cirurgião que não precisa se vender — só se explicar. O site deve parecer entrar em uma clínica bem iluminada e silenciosa: tudo no lugar, nada supérfluo, confiança completa em cada detalhe.

---

*Após gerar o HTML, substituir:*
- *Foto do Dr. Mateus (ensaio profissional)*
- *Fotos da clínica (5 imagens)*
- *Endereço completo + links Waze e Google Maps*
- *CRM número (confirmar)*
- *Logos dos convênios em SVG (arquivos PNG normalizados disponíveis em `img/convenios/normalized/`)*
- *og-cover.jpg (imagem 1200×630px para compartilhamento)*
