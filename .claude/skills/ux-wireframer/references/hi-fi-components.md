# Hi-Fi Component Patterns

Reusable HTML/CSS component snippets for hi-fi mockups. All use CSS variables — define them in `:root` before using.

---

## CSS Variable Template

```css
:root {
  /* Brand */
  --primary: #C9A84C;        /* Main accent / CTA color */
  --primary-dark: #9A7535;
  --primary-light: #E2C97E;
  --bg-dark: #0E1628;
  --bg-mid: #162035;
  --bg-light: #F5EDD8;
  --text-main: #FFFFFF;
  --text-muted: rgba(255,255,255,0.6);
  --text-dark: #1A1A2E;

  /* Spacing */
  --max-width: 860px;
  --section-y: 80px;
  --gap-md: 24px;
  --gap-lg: 48px;

  /* Shape */
  --radius-sm: 6px;
  --radius-md: 12px;
  --radius-lg: 20px;
  --radius-pill: 999px;

  /* Typography */
  --font-display: 'Playfair Display', Georgia, serif;
  --font-body: 'Lato', system-ui, sans-serif;
  --font-label: 'Cinzel', Georgia, serif;
}
```

---

## Topbar

```html
<div class="topbar">
  🔥 Acesso imediato · Garantia de 7 dias · +2.300 cristãos transformados
</div>
```

```css
.topbar {
  background: var(--primary-dark);
  color: var(--bg-dark);
  text-align: center;
  padding: 10px 24px;
  font-size: 13px;
  font-weight: 700;
  letter-spacing: 1px;
  text-transform: uppercase;
}
```

---

## Section Wrapper

```html
<section class="section section--dark" id="hero">
  <div class="container">
    <!-- content -->
  </div>
</section>
```

```css
.section {
  padding: var(--section-y) 24px;
}
.section--dark  { background: var(--bg-dark); color: var(--text-main); }
.section--mid   { background: var(--bg-mid);  color: var(--text-main); }
.section--light { background: var(--bg-light); color: var(--text-dark); }
.section--cream { background: #FBF5E6; color: var(--text-dark); }

.container {
  max-width: var(--max-width);
  margin: 0 auto;
}
```

---

## Eyebrow Label

```html
<span class="eyebrow">Apresentando</span>
```

```css
.eyebrow {
  display: inline-block;
  font-family: var(--font-label);
  font-size: 11px;
  letter-spacing: 3px;
  text-transform: uppercase;
  color: var(--primary);
  border: 1px solid rgba(201,168,76,0.4);
  padding: 6px 18px;
  border-radius: 2px;
  margin-bottom: 24px;
}
```

---

## Hero Headline + Subheadline

```html
<h1 class="hero-title">
  Por que cristãos que oram continuam
  <em>atraindo as pessoas erradas</em>
</h1>
<p class="hero-sub">
  Não é falta de fé. É um padrão que ninguém te ensinou a quebrar.
</p>
```

```css
.hero-title {
  font-family: var(--font-display);
  font-size: clamp(28px, 5vw, 52px);
  font-weight: 900;
  line-height: 1.15;
  color: #fff;
  margin-bottom: 20px;
}
.hero-title em {
  font-style: italic;
  color: var(--primary-light);
}
.hero-sub {
  font-size: clamp(16px, 2.5vw, 20px);
  color: var(--text-muted);
  line-height: 1.65;
  max-width: 580px;
  margin: 0 auto 40px;
}
```

---

## CTA Button (Primary)

```html
<a href="#offer" class="btn btn--primary">
  QUERO ACESSAR OS 21 PASSOS AGORA →
</a>
<p class="btn-sub">de R$97 por apenas R$47 · Acesso imediato</p>
```

```css
.btn {
  display: inline-block;
  padding: 18px 44px;
  font-size: 16px;
  font-weight: 700;
  letter-spacing: 0.5px;
  text-decoration: none;
  border-radius: var(--radius-sm);
  transition: transform 0.15s, box-shadow 0.15s;
  cursor: pointer;
}
.btn--primary {
  background: var(--primary);
  color: var(--bg-dark);
  box-shadow: 0 4px 24px rgba(201,168,76,0.35);
}
.btn--primary:hover {
  transform: translateY(-2px);
  box-shadow: 0 8px 32px rgba(201,168,76,0.5);
}
.btn-sub {
  font-size: 13px;
  color: var(--text-muted);
  margin-top: 12px;
  text-align: center;
}
```

---

## Pain Point List (with ❌ markers)

```html
<ul class="pain-list">
  <li>Carregar sozinho os problemas emocionais do outro</li>
  <li>Confundir intensidade dos sentimentos com direção de Deus</li>
  <li>Ignorar sinais óbvios por ver o potencial que a pessoa poderia ter</li>
</ul>
```

```css
.pain-list {
  list-style: none;
  padding: 0;
  display: flex;
  flex-direction: column;
  gap: 14px;
  max-width: 640px;
  margin: 24px auto;
}
.pain-list li {
  display: flex;
  align-items: flex-start;
  gap: 12px;
  font-size: 16px;
  line-height: 1.5;
  color: rgba(255,255,255,0.85);
}
.pain-list li::before {
  content: "❌";
  flex-shrink: 0;
  margin-top: 2px;
}
```

---

## Benefits Grid (icon + title + description)

```html
<div class="benefits-grid">
  <div class="benefit-card">
    <div class="benefit-icon">🔍</div>
    <h3>Discernimento real</h3>
    <p>Como distinguir essência de aparência antes de se envolver emocionalmente.</p>
  </div>
  <!-- repeat -->
</div>
```

```css
.benefits-grid {
  display: grid;
  grid-template-columns: repeat(auto-fit, minmax(240px, 1fr));
  gap: 24px;
  margin-top: 48px;
}
.benefit-card {
  background: rgba(255,255,255,0.04);
  border: 1px solid rgba(201,168,76,0.15);
  border-radius: var(--radius-md);
  padding: 28px 24px;
}
.benefit-icon {
  font-size: 28px;
  margin-bottom: 12px;
}
.benefit-card h3 {
  font-size: 17px;
  font-weight: 700;
  color: var(--primary-light);
  margin-bottom: 8px;
}
.benefit-card p {
  font-size: 15px;
  line-height: 1.6;
  color: var(--text-muted);
}
```

---

## Testimonial Card

```html
<div class="testimonial-card">
  <p class="testimonial-quote">
    "Depois dos passos, entendi que estava escolhendo com as minhas feridas.
    Hoje tenho clareza que nunca tive antes."
  </p>
  <div class="testimonial-author">
    <div class="testimonial-avatar">M</div>
    <div>
      <strong>Mariana S.</strong>
      <span>São Paulo, SP</span>
    </div>
  </div>
</div>
```

```css
.testimonial-card {
  background: rgba(255,255,255,0.05);
  border-left: 3px solid var(--primary);
  border-radius: var(--radius-sm);
  padding: 28px;
  text-align: left;
}
.testimonial-quote {
  font-size: 16px;
  line-height: 1.7;
  color: rgba(255,255,255,0.85);
  font-style: italic;
  margin-bottom: 20px;
}
.testimonial-author {
  display: flex;
  align-items: center;
  gap: 12px;
}
.testimonial-avatar {
  width: 40px; height: 40px;
  border-radius: 50%;
  background: var(--primary-dark);
  color: var(--bg-dark);
  font-weight: 700;
  display: flex; align-items: center; justify-content: center;
}
.testimonial-author strong { display: block; font-size: 15px; }
.testimonial-author span  { font-size: 13px; color: var(--text-muted); }
```

---

## Price Block

```html
<div class="price-block">
  <span class="price-original">De R$97</span>
  <div class="price-current">
    <span class="price-currency">R$</span>
    <span class="price-amount">47</span>
  </div>
  <p class="price-note">Acesso imediato · Formato digital</p>
  <a href="#" class="btn btn--primary">QUERO ACESSAR OS 21 PASSOS AGORA →</a>
  <p class="payment-icons">🔒 Pix · Cartão de crédito · Boleto</p>
</div>
```

```css
.price-block {
  text-align: center;
  padding: 48px 24px;
}
.price-original {
  font-size: 18px;
  color: var(--text-muted);
  text-decoration: line-through;
}
.price-current {
  display: flex;
  align-items: flex-start;
  justify-content: center;
  gap: 4px;
  margin: 8px 0 4px;
}
.price-currency {
  font-size: 28px;
  font-weight: 700;
  margin-top: 12px;
  color: var(--primary-light);
}
.price-amount {
  font-size: 80px;
  font-weight: 900;
  line-height: 1;
  color: var(--primary-light);
  font-family: var(--font-display);
}
.price-note {
  font-size: 14px;
  color: var(--text-muted);
  margin-bottom: 28px;
}
.payment-icons {
  font-size: 13px;
  color: var(--text-muted);
  margin-top: 14px;
}
```

---

## Guarantee Badge

```html
<div class="guarantee">
  <div class="guarantee-seal">🛡️</div>
  <div>
    <h3>Garantia de 7 dias</h3>
    <p>Se o conteúdo não te trouxer clareza, devolvemos 100% do seu investimento. Sem perguntas.</p>
  </div>
</div>
```

```css
.guarantee {
  display: flex;
  align-items: center;
  gap: 24px;
  background: rgba(255,255,255,0.04);
  border: 1px solid rgba(201,168,76,0.2);
  border-radius: var(--radius-md);
  padding: 32px;
  max-width: 640px;
  margin: 0 auto;
}
.guarantee-seal { font-size: 48px; flex-shrink: 0; }
.guarantee h3 {
  font-size: 20px;
  font-weight: 700;
  color: var(--primary-light);
  margin-bottom: 8px;
}
.guarantee p {
  font-size: 15px;
  line-height: 1.6;
  color: var(--text-muted);
}
```

---

## FAQ Accordion

```html
<div class="faq-list">
  <details class="faq-item">
    <summary>Esse conteúdo é só para mulheres?</summary>
    <p>Não. Os 21 passos foram desenvolvidos para cristãos — homens e mulheres...</p>
  </details>
</div>
```

```css
.faq-list {
  max-width: 680px;
  margin: 0 auto;
  display: flex;
  flex-direction: column;
  gap: 12px;
}
.faq-item {
  background: rgba(255,255,255,0.04);
  border: 1px solid rgba(201,168,76,0.15);
  border-radius: var(--radius-sm);
  overflow: hidden;
}
.faq-item summary {
  padding: 20px 24px;
  cursor: pointer;
  font-weight: 600;
  font-size: 16px;
  list-style: none;
  display: flex;
  justify-content: space-between;
  align-items: center;
}
.faq-item summary::after {
  content: "+";
  font-size: 20px;
  color: var(--primary);
  transition: transform 0.2s;
}
.faq-item[open] summary::after {
  transform: rotate(45deg);
}
.faq-item p {
  padding: 0 24px 20px;
  font-size: 15px;
  line-height: 1.65;
  color: var(--text-muted);
}
```

---

## Section Divider

```html
<div class="divider"></div>
```

```css
.divider {
  width: 80px;
  height: 2px;
  background: var(--primary);
  margin: 0 auto 40px;
  opacity: 0.6;
}
```

---

## Blockquote / Callout

```html
<blockquote class="callout">
  "Você não precisa de várias opções. Você precisa de clareza do céu."
</blockquote>
```

```css
.callout {
  border-left: 4px solid var(--primary);
  padding: 20px 28px;
  margin: 32px 0;
  background: rgba(201,168,76,0.06);
  border-radius: 0 var(--radius-sm) var(--radius-sm) 0;
  font-size: 18px;
  font-style: italic;
  line-height: 1.65;
  color: rgba(255,255,255,0.85);
}
```

---

## Responsive Utilities

```css
@media (max-width: 640px) {
  :root {
    --section-y: 56px;
  }
  .hero-title { font-size: 28px; }
  .benefits-grid { grid-template-columns: 1fr; }
  .guarantee { flex-direction: column; text-align: center; }
  .btn { width: 100%; text-align: center; padding: 18px 24px; }
}
```
