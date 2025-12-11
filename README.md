# Universal CSS Template - Entwickler-Dokumentation

Ein **universelles, app-agnostisches CSS-Template** basierend auf Tailwind CSS v4 mit wiederverwendbaren Komponenten-Klassen.

## Inhaltsverzeichnis

1. [Schnellstart](#schnellstart)
2. [Installation](#installation)
3. [Build-Befehle](#build-befehle)
4. [Architektur](#architektur)
5. [CSS Custom Properties](#css-custom-properties)
6. [Komponenten-Referenz](#komponenten-referenz)
7. [Dark Mode](#dark-mode)
8. [Anpassung für eigene Projekte](#anpassung-für-eigene-projekte)
9. [Best Practices](#best-practices)

---

## Schnellstart

```bash
# 1. Repository klonen
git clone https://github.com/z-komm/universal-css-template.git
cd universal-css-template

# 2. Dependencies installieren
npm install

# 3. CSS kompilieren
npm run build-css

# 4. In HTML einbinden
```

```html
<!-- Fonts (optional, für Inter Font) -->
<link rel="stylesheet" href="assets/css/fonts.css">
<!-- Tailwind CSS (compiled) -->
<link rel="stylesheet" href="assets/css/tailwind.css">
<!-- Font Awesome Icons (local) -->
<link rel="stylesheet" href="assets/css/fontawesome.min.css">
```

---

## Installation

### Voraussetzungen

- Node.js 18+
- npm 9+

### Dependencies

```json
{
  "devDependencies": {
    "tailwindcss": "^4.1.12"
  },
  "dependencies": {
    "@tailwindcss/cli": "^4.1.17"
  }
}
```

### Setup für neues Projekt

```bash
# Initialisierung
npm init -y
npm install tailwindcss @tailwindcss/cli

# Dateien kopieren
cp src/styles.css <dein-projekt>/src/
cp tailwind.config.js <dein-projekt>/
```

---

## Build-Befehle

| Befehl | Beschreibung |
|--------|--------------|
| `npm run build-css` | Einmaliger Build |
| `npm run build-css:watch` | Watch-Mode für Entwicklung |
| `npm run build-css:minify` | Minified Build für Produktion |

### Watch-Mode starten

```bash
npm run build-css:watch
```

> Der Watcher erkennt automatisch Änderungen in PHP, HTML, JS und CSS-Dateien und kompiliert das CSS neu.

---

## Architektur

### Dateistruktur

```
projekt/
├── src/
│   └── styles.css              # Source CSS mit Custom Properties & Components
├── assets/
│   ├── css/
│   │   ├── tailwind.css        # Kompiliertes CSS (generiert)
│   │   ├── fonts.css           # Inter Font @font-face Definitionen
│   │   └── fontawesome.min.css # Font Awesome Icons (lokal)
│   ├── fonts/
│   │   ├── Inter-Regular.woff2
│   │   ├── Inter-Medium.woff2
│   │   ├── Inter-SemiBold.woff2
│   │   └── Inter-Bold.woff2
│   └── webfonts/               # Font Awesome Webfonts
│       ├── fa-brands-400.woff2
│       ├── fa-regular-400.woff2
│       └── fa-solid-900.woff2
├── tailwind.config.js          # Tailwind Konfiguration
└── package.json                # npm Scripts
```

### CSS-Aufbau (src/styles.css)

```css
/* 1. Tailwind Import */
@import "tailwindcss";

/* 2. CSS Custom Properties */
:root { ... }

/* 3. Dark Mode Variables */
.dark { ... }

/* 4. Base Layer */
@layer base { ... }

/* 5. Components Layer */
@layer components { ... }

/* 6. Utilities Layer */
@layer utilities { ... }
```

---

## CSS Custom Properties

Alle Design-Tokens sind als CSS Variables definiert und können einfach überschrieben werden.

### Brand Colors

```css
:root {
  --color-brand: #0077B5;         /* Primärfarbe */
  --color-brand-light: #00A0DC;   /* Helle Variante */
  --color-brand-dark: #005885;    /* Dunkle Variante */
  --color-brand-contrast: #ffffff; /* Text auf Brand */
}
```

**Anpassung für dein Projekt:**

```css
:root {
  --color-brand: #FF5722;         /* Dein Orange */
  --color-brand-light: #FF8A65;
  --color-brand-dark: #E64A19;
}
```

### Semantic Colors

```css
--color-success: #10b981;    /* Grün */
--color-warning: #f59e0b;    /* Gelb/Orange */
--color-danger: #ef4444;     /* Rot */
--color-info: #3b82f6;       /* Blau */
```

### Surface & Text Colors

```css
/* Hintergründe */
--bg-primary: #ffffff;
--bg-secondary: #f9fafb;
--bg-tertiary: #f3f4f6;
--bg-elevated: #ffffff;

/* Text */
--text-primary: #111827;
--text-secondary: #4b5563;
--text-muted: #9ca3af;
```

### Spacing & Typography

```css
/* Abstände */
--spacing-xs: 0.25rem;   /* 4px */
--spacing-sm: 0.5rem;    /* 8px */
--spacing: 1rem;         /* 16px */
--spacing-md: 1.5rem;    /* 24px */
--spacing-lg: 2rem;      /* 32px */
--spacing-xl: 3rem;      /* 48px */

/* Schriftgrößen */
--font-size-xs: 0.75rem;    /* 12px */
--font-size-sm: 0.875rem;   /* 14px */
--font-size-base: 1rem;     /* 16px */
--font-size-lg: 1.125rem;   /* 18px */
--font-size-xl: 1.25rem;    /* 20px */
```

### Shadows & Borders

```css
/* Schatten */
--shadow-sm: 0 1px 2px 0 rgb(0 0 0 / 0.05);
--shadow: 0 1px 3px 0 rgb(0 0 0 / 0.1);
--shadow-md: 0 4px 6px -1px rgb(0 0 0 / 0.1);
--shadow-lg: 0 10px 15px -3px rgb(0 0 0 / 0.1);

/* Border Radius */
--border-radius-sm: 0.25rem;   /* 4px */
--border-radius: 0.375rem;     /* 6px */
--border-radius-md: 0.5rem;    /* 8px */
--border-radius-lg: 0.75rem;   /* 12px */
--border-radius-xl: 1rem;      /* 16px */
```

---

## Komponenten-Referenz

### Buttons

```html
<!-- Primär -->
<button class="btn-primary">Primär</button>

<!-- Sekundär -->
<button class="btn-secondary">Sekundär</button>

<!-- Weitere Varianten -->
<button class="btn-success">Erfolg</button>
<button class="btn-danger">Gefahr</button>
<button class="btn-warning">Warnung</button>
<button class="btn-ghost">Ghost</button>
<button class="btn-outline">Outline</button>
<button class="btn-link">Link</button>

<!-- Größen -->
<button class="btn-primary btn-sm">Klein</button>
<button class="btn-primary btn-lg">Groß</button>
<button class="btn-primary btn-xl">Extra Groß</button>
<button class="btn-primary btn-full">Volle Breite</button>

<!-- Icon Button -->
<button class="btn-icon"><i class="fas fa-cog"></i></button>

<!-- Loading State -->
<button class="btn-primary btn-loading">Lädt...</button>
```

### Cards

```html
<div class="card">
  <div class="card-header">
    <h3>Titel</h3>
  </div>
  <div class="card-body">
    Inhalt hier...
  </div>
  <div class="card-footer">
    Footer-Aktionen
  </div>
</div>

<!-- Varianten -->
<div class="card-stat">Statistik Card</div>
<div class="card-action">Klickbare Card</div>
```

### Alerts

```html
<div class="alert-success">
  <i class="alert-icon fas fa-check-circle"></i>
  <span class="alert-text">Erfolgsmeldung</span>
</div>

<div class="alert-error">Fehlermeldung</div>
<div class="alert-warning">Warnung</div>
<div class="alert-info">Information</div>
```

### Forms

```html
<div class="form-group">
  <label class="form-label">E-Mail</label>
  <input type="email" class="form-input" placeholder="email@example.com">
  <p class="form-help">Hilfetext hier</p>
</div>

<div class="form-group">
  <label class="form-label">Auswahl</label>
  <select class="form-select">
    <option>Option 1</option>
    <option>Option 2</option>
  </select>
</div>

<div class="form-group">
  <label class="form-label">Nachricht</label>
  <textarea class="form-textarea" rows="4"></textarea>
</div>

<!-- Fehler-Zustand -->
<input type="text" class="form-input form-error">
<p class="form-error-text">Fehlertext</p>

<!-- Checkbox/Radio -->
<input type="checkbox" class="form-checkbox">
<input type="radio" class="form-radio">
```

### Badges

```html
<span class="badge badge-primary">Primary</span>
<span class="badge badge-success">Success</span>
<span class="badge badge-warning">Warning</span>
<span class="badge badge-danger">Danger</span>
<span class="badge badge-info">Info</span>
<span class="badge badge-gray">Gray</span>
```

### Navigation

```html
<nav class="brand-gradient">
  <a href="#" class="nav-link">Link 1</a>
  <a href="#" class="nav-link-active">Aktiv</a>
  <a href="#" class="nav-link">Link 3</a>
</nav>
```

### Tables

```html
<table class="table">
  <thead class="table-header">
    <tr>
      <th class="table-th">Spalte 1</th>
      <th class="table-th">Spalte 2</th>
    </tr>
  </thead>
  <tbody>
    <tr class="table-row">
      <td class="table-td">Wert 1</td>
      <td class="table-td">Wert 2</td>
    </tr>
  </tbody>
</table>
```

### Modals

```html
<div class="modal-backdrop">
  <div class="modal">
    <div class="modal-header">
      <h3>Modal Titel</h3>
      <button class="btn-icon">×</button>
    </div>
    <div class="modal-body">
      Inhalt...
    </div>
    <div class="modal-footer">
      <button class="btn-secondary">Abbrechen</button>
      <button class="btn-primary">Bestätigen</button>
    </div>
  </div>
</div>
```

### Progress & Loading

```html
<!-- Progress Bar -->
<div class="progress">
  <div class="progress-bar progress-brand" style="width: 75%"></div>
</div>

<!-- Spinner -->
<div class="spinner"></div>
<div class="spinner spinner-sm"></div>
<div class="spinner spinner-lg"></div>

<!-- Skeleton -->
<div class="skeleton skeleton-text"></div>
<div class="skeleton skeleton-circle" style="width: 48px; height: 48px;"></div>
```

### Tooltips

```html
<div class="tooltip">
  Hover mich
  <div class="tooltip-text">Tooltip-Inhalt hier</div>
</div>
```

### Empty States

```html
<div class="empty-state">
  <div class="empty-state-icon">
    <i class="fas fa-inbox"></i>
  </div>
  <h3 class="empty-state-title">Keine Daten</h3>
  <p class="empty-state-text">Noch keine Einträge vorhanden.</p>
  <div class="empty-state-action">
    <button class="btn-primary">Erstellen</button>
  </div>
</div>
```

### Calendar & Planner (App-spezifisch)

```html
<!-- Calendar Grid -->
<div class="calendar-grid">
  <div class="drop-zone" data-date="2024-01-15">
    <div class="post-card" draggable="true">
      <div class="status-scheduled"></div>
      Geplanter Post
    </div>
  </div>
</div>

<!-- Status Badges -->
<span class="status-published">Veröffentlicht</span>
<span class="status-scheduled">Geplant</span>
<span class="status-draft">Entwurf</span>
<span class="status-failed">Fehlgeschlagen</span>

<!-- Time Badges -->
<span class="recommended-time">09:00</span>
<span class="optimal-time">17:00</span>
```

### Media Upload

```html
<div class="media-upload-zone">
  <input type="file" hidden>
  <i class="fas fa-cloud-upload-alt"></i>
  <p>Dateien hier ablegen</p>
</div>
```

### Social Preview

```html
<div class="linkedin-post-preview">
  <div class="linkedin-preview-header">
    <div class="linkedin-preview-avatar"></div>
    <div>Name</div>
  </div>
  <div class="linkedin-preview-content">
    Post-Inhalt mit <span class="hashtag">#Hashtag</span>
  </div>
</div>
```

---

## Dark Mode

Das System unterstützt drei Dark-Mode-Varianten:

### 1. Manuelle Klasse

```html
<html class="dark">
  <!-- Dark Mode aktiviert -->
</html>
```

### 2. Data-Attribut

```html
<html data-theme="dark">
  <!-- Dark Mode aktiviert -->
</html>

<html data-theme="light">
  <!-- Light Mode erzwungen -->
</html>
```

### 3. System-Präferenz (automatisch)

```css
@media (prefers-color-scheme: dark) {
  /* Automatisch Dark Mode wenn System-Einstellung */
}
```

### Dark Mode Toggle (JavaScript)

```javascript
function toggleDarkMode() {
  const html = document.documentElement;
  const currentTheme = html.getAttribute('data-theme');

  if (currentTheme === 'dark') {
    html.setAttribute('data-theme', 'light');
    html.classList.remove('dark');
    localStorage.setItem('theme', 'light');
  } else {
    html.setAttribute('data-theme', 'dark');
    html.classList.add('dark');
    localStorage.setItem('theme', 'dark');
  }
}

// Beim Laden wiederherstellen (respektiert System-Präferenz)
(function() {
  const savedTheme = localStorage.getItem('theme');
  const prefersDark = window.matchMedia('(prefers-color-scheme: dark)').matches;
  const theme = savedTheme || (prefersDark ? 'dark' : 'light');

  document.documentElement.setAttribute('data-theme', theme);
  if (theme === 'dark') {
    document.documentElement.classList.add('dark');
  }
})();
```

> **Wichtig:** Das `data-theme` Attribut ist notwendig, um die System-Präferenz (`prefers-color-scheme`) zu überschreiben. Die CSS-Regel `@media (prefers-color-scheme: dark)` greift nur, wenn `data-theme="light"` **nicht** gesetzt ist.

### Smooth Scroll mit Sticky-Nav Offset

Bei sticky Navigation werden Anker-Ziele von der Nav verdeckt. Dieses Script scrollt mit korrektem Offset:

```javascript
// Smooth scroll with offset for sticky nav
// navId = ID des sticky Nav-Elements
function initSmoothScroll(navId = 'mainNav') {
  document.querySelectorAll('a[href^="#"]').forEach(anchor => {
    anchor.addEventListener('click', function(e) {
      const targetId = this.getAttribute('href');
      if (targetId === '#') return;

      const target = document.querySelector(targetId);
      if (target) {
        e.preventDefault();
        const nav = document.getElementById(navId);
        const navHeight = nav ? nav.offsetHeight : 0;
        const targetPosition = target.getBoundingClientRect().top + window.scrollY - navHeight - 16;

        window.scrollTo({
          top: targetPosition,
          behavior: 'smooth'
        });

        history.pushState(null, null, targetId);
      }
    });
  });
}

// Initialisieren
initSmoothScroll('mainNav');
```

> **Hinweis:** Das CSS enthält bereits `scroll-margin-top: 5rem` für `[id]` Elemente als Fallback, aber JavaScript ist zuverlässiger bei `scroll-behavior: smooth`.

---

## Anpassung für eigene Projekte

### 1. Brand Colors ändern

Erstelle eine eigene CSS-Datei, die nach dem Haupt-CSS geladen wird:

```css
/* custom.css */
:root {
  --color-brand: #6366F1;         /* Indigo */
  --color-brand-light: #818CF8;
  --color-brand-dark: #4F46E5;
}
```

### 2. tailwind.config.js anpassen

```javascript
module.exports = {
  content: [
    "./*.html",
    "./*.php",
    "./src/**/*.{js,jsx,ts,tsx}",
    // Deine Pfade hier
  ],
  darkMode: 'class',
  theme: {
    extend: {
      colors: {
        brand: {
          DEFAULT: '#6366F1',
          light: '#818CF8',
          dark: '#4F46E5',
        },
      },
    }
  },
}
```

### 3. Neue Komponenten hinzufügen

Füge in `src/styles.css` im `@layer components` Block hinzu:

```css
@layer components {
  /* Deine Custom Components */
  .my-custom-button {
    @apply px-4 py-2 rounded-lg;
    background: var(--color-brand);
    color: white;
  }
}
```

---

## Best Practices

### 1. Utility-First mit Komponenten-Klassen

```html
<!-- Gut: Komponenten-Klasse für wiederkehrende Patterns -->
<button class="btn-primary">Speichern</button>

<!-- Gut: Utilities für einmalige Anpassungen -->
<button class="btn-primary mt-4">Speichern</button>

<!-- Vermeiden: Lange Utility-Ketten für wiederkehrende Patterns -->
<button class="inline-flex items-center px-4 py-2 bg-blue-600 text-white rounded-lg hover:bg-blue-700">
  Speichern
</button>
```

### 2. Theme-Aware Utility-Klassen verwenden

Für Dark Mode kompatible Farben nutze die `text-theme-*` und `bg-theme-*` Klassen:

```html
<!-- Gut: Theme-aware Klassen (reagieren auf Dark Mode) -->
<p class="text-theme-primary">Haupttext</p>
<p class="text-theme-secondary">Sekundärtext</p>
<p class="text-theme-muted">Dezenter Text</p>
<div class="bg-theme-primary">Primärer Hintergrund</div>
<div class="bg-theme-secondary">Sekundärer Hintergrund</div>
<div class="border border-theme">Rahmen</div>

<!-- Vermeiden: Hardcoded Tailwind Colors (ändern sich nicht im Dark Mode) -->
<p class="text-gray-600">Funktioniert nicht im Dark Mode</p>
<div class="bg-white">Bleibt immer weiß</div>
```

### 3. CSS Variables in Custom Styles

```css
/* Gut: Variable nutzen */
.my-element {
  color: var(--text-primary);
  background: var(--bg-secondary);
}

/* Vermeiden: Hardcoded Colors */
.my-element {
  color: #111827;
  background: #f9fafb;
}
```

### 4. Responsive Design

```html
<!-- Mobile-First Approach -->
<div class="grid grid-cols-1 md:grid-cols-2 lg:grid-cols-3 gap-4">
  <!-- Cards -->
</div>
```

### 5. Semantic HTML mit CSS-Klassen

```html
<!-- Gut -->
<nav class="brand-gradient">
  <a href="/" class="nav-link-active">Home</a>
</nav>

<!-- Vermeiden -->
<div class="brand-gradient">
  <span class="nav-link-active" onclick="...">Home</span>
</div>
```

---

## Dateien für GitHub

Folgende Dateien sollten ins Repository:

```
├── src/
│   └── styles.css              # Source CSS mit Custom Properties & Components
├── assets/
│   ├── css/
│   │   ├── tailwind.css        # Kompiliertes CSS (generiert)
│   │   ├── fonts.css           # Inter Font @font-face
│   │   └── fontawesome.min.css # Font Awesome Icons
│   ├── fonts/                  # Inter Webfonts
│   └── webfonts/               # Font Awesome Webfonts
├── demo.html                   # Komponenten-Showcase
├── tailwind.config.js          # Tailwind Konfiguration
├── package.json                # Dependencies & Scripts
├── README.md                   # Diese Dokumentation
└── .gitignore                  # node_modules ausschließen
```

### .gitignore

```
node_modules/
.DS_Store
*.log
```

---

## Support & Weiterentwicklung

### Neue Komponente hinzufügen

1. Definiere in `src/styles.css` im `@layer components`
2. Führe `npm run build-css` aus
3. Teste die Komponente
4. Dokumentiere in der README.md

### Bug melden

Issues im GitHub Repository erstellen mit:
- Browser & Version
- Reproduzierbare Schritte
- Erwartetes vs. tatsächliches Verhalten

---

**Version:** 1.0.0
**Tailwind CSS:** v4.1.17
**Letzte Aktualisierung:** Dezember 2024
