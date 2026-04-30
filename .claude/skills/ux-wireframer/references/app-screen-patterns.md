# App Screen & Dashboard Patterns

## Default App Layout

```
┌─────────────────────────────────────────┐
│  Topbar / Header (fixed)                │
├──────────┬──────────────────────────────┤
│          │                              │
│ Sidebar  │   Main Content Area          │
│ (nav)    │                              │
│          │                              │
└──────────┴──────────────────────────────┘
```

**Sidebar width:** 220–260px  
**Content area:** fluid, max 1200px  
**Header height:** 56–64px  

---

## Dashboard Grid

Use CSS Grid for the main content layout:

```css
.dashboard-grid {
  display: grid;
  grid-template-columns: repeat(12, 1fr);
  gap: 20px;
  padding: 24px;
}

/* Full width */
.col-12 { grid-column: span 12; }
/* Half */
.col-6  { grid-column: span 6; }
/* Third */
.col-4  { grid-column: span 4; }
/* Quarter */
.col-3  { grid-column: span 3; }

@media (max-width: 768px) {
  .col-6, .col-4, .col-3 { grid-column: span 12; }
}
```

---

## Stat Card

```html
<div class="stat-card">
  <span class="stat-label">Total Vendas</span>
  <span class="stat-value">R$ 14.320</span>
  <span class="stat-delta positive">+12% este mês</span>
</div>
```

```css
.stat-card {
  background: var(--surface);
  border: 1px solid var(--border);
  border-radius: 12px;
  padding: 24px;
  display: flex;
  flex-direction: column;
  gap: 6px;
}
.stat-label { font-size: 13px; color: var(--text-muted); text-transform: uppercase; letter-spacing: 0.5px; }
.stat-value { font-size: 32px; font-weight: 700; color: var(--text-main); }
.stat-delta { font-size: 13px; font-weight: 600; }
.stat-delta.positive { color: #27AE60; }
.stat-delta.negative { color: #E74C3C; }
```

---

## Data Table

```html
<table class="data-table">
  <thead>
    <tr>
      <th>Nome</th>
      <th>Status</th>
      <th>Valor</th>
    </tr>
  </thead>
  <tbody>
    <tr>
      <td>Mariana Santos</td>
      <td><span class="badge badge--green">Ativo</span></td>
      <td>R$47,00</td>
    </tr>
  </tbody>
</table>
```

```css
.data-table { width: 100%; border-collapse: collapse; font-size: 14px; }
.data-table th {
  text-align: left; padding: 12px 16px;
  font-weight: 600; color: var(--text-muted);
  border-bottom: 2px solid var(--border);
}
.data-table td { padding: 14px 16px; border-bottom: 1px solid var(--border); }
.data-table tr:hover td { background: var(--surface-hover); }
```

---

## Badge

```css
.badge {
  display: inline-flex;
  align-items: center;
  padding: 3px 10px;
  border-radius: 999px;
  font-size: 12px;
  font-weight: 600;
}
.badge--green  { background: rgba(39,174,96,0.15);  color: #27AE60; }
.badge--red    { background: rgba(231,76,60,0.15);   color: #E74C3C; }
.badge--yellow { background: rgba(241,196,15,0.15);  color: #D4AC0D; }
.badge--blue   { background: rgba(52,152,219,0.15);  color: #2E86C1; }
```

---

## Sidebar Nav

```html
<nav class="sidebar">
  <div class="sidebar-logo">App</div>
  <ul class="sidebar-nav">
    <li class="active"><a href="#">📊 Dashboard</a></li>
    <li><a href="#">👥 Usuários</a></li>
    <li><a href="#">📦 Produtos</a></li>
    <li><a href="#">⚙️ Config</a></li>
  </ul>
</nav>
```

```css
.sidebar {
  width: 240px;
  height: 100vh;
  background: var(--bg-dark);
  border-right: 1px solid var(--border);
  position: fixed;
  top: 0; left: 0;
  display: flex;
  flex-direction: column;
  padding: 24px 0;
}
.sidebar-logo { padding: 0 24px 24px; font-weight: 700; font-size: 18px; }
.sidebar-nav { list-style: none; padding: 0; margin: 0; }
.sidebar-nav li a {
  display: block;
  padding: 12px 24px;
  color: var(--text-muted);
  text-decoration: none;
  font-size: 14px;
  transition: background 0.15s, color 0.15s;
}
.sidebar-nav li.active a,
.sidebar-nav li a:hover {
  background: rgba(255,255,255,0.06);
  color: var(--text-main);
}
```

---

## Multi-Step / Funnel Flow

For multi-screen flows, render each screen as a tab:

```html
<div class="screen-tabs">
  <div class="tab-nav">
    <button class="tab-btn active" onclick="showTab('step1')">Tela 1</button>
    <button class="tab-btn" onclick="showTab('step2')">Tela 2</button>
  </div>
  <div id="step1" class="tab-content active"><!-- screen 1 --></div>
  <div id="step2" class="tab-content"><!-- screen 2 --></div>
</div>
```

```javascript
function showTab(id) {
  document.querySelectorAll('.tab-content').forEach(el => el.classList.remove('active'));
  document.querySelectorAll('.tab-btn').forEach(el => el.classList.remove('active'));
  document.getElementById(id).classList.add('active');
  event.target.classList.add('active');
}
```
