# platform-ui

A lightweight, self-contained CSS design system for internal platform tools.

No framework. No build step. No external dependencies. Drop one file into any app and go.

---

## Quick start

```bash
# Copy into your app
cp platform-ui.css your-app/static/platform-ui.css
```

```html
<!-- Reference in your HTML -->
<link rel="stylesheet" href="/static/platform-ui.css"/>
```

That's it. No npm, no bundler, no CDN.

---

## Usage

### Minimal page template

```html
<!DOCTYPE html>
<html lang="en">
<head>
  <meta charset="UTF-8"/>
  <meta name="viewport" content="width=device-width, initial-scale=1.0"/>
  <link rel="icon" type="image/svg+xml" href="/static/favicon.svg"/>
  <link rel="stylesheet" href="/static/platform-ui.css"/>
  <title>My App</title>
</head>
<body>

<header class="pf-header">
  <a class="pf-logo" href="/">
    <div class="pf-logo-icon">MA</div>
    <span class="pf-logo-text">My<span>App</span></span>
  </a>
  <nav class="pf-nav">
    <a href="/page1" class="active">Page 1</a>
    <a href="/page2">Page 2</a>
  </nav>
</header>

<div class="page-content container">
  <!-- your content here -->
</div>

</body>
</html>
```

Open `demo.html` in a browser to see all components.

---

## Components

### Header

```html
<header class="pf-header">
  <a class="pf-logo" href="/">
    <div class="pf-logo-icon">SH</div>
    <span class="pf-logo-text">Schema<span>Hub</span></span>
  </a>
  <nav class="pf-nav">
    <a href="/ui">Generator</a>
    <a href="/builder" class="active">Builder</a>
    <a href="/docs">API Docs</a>
  </nav>
</header>
```

### Buttons

```html
<button class="btn btn-primary">Primary</button>
<button class="btn btn-secondary">Secondary</button>
<button class="btn btn-ghost">Ghost</button>
<button class="btn btn-success">Success</button>
<button class="btn btn-danger">Danger</button>
<button class="btn btn-violet">Violet</button>

<!-- Sizes -->
<button class="btn btn-primary btn-sm">Small</button>
<button class="btn btn-primary btn-lg">Large</button>

<!-- Disabled -->
<button class="btn btn-primary" disabled>Disabled</button>
```

### Cards

```html
<div class="card">Basic card</div>
<div class="card card-blue">Blue accent</div>
<div class="card card-hoverable">Hoverable card</div>

<!-- Stat card -->
<div class="stat-card">
  <div class="stat-value">1,024</div>
  <div class="stat-label">Total Requests</div>
  <div class="stat-delta up">↑ 12% today</div>
</div>
```

### Badges

```html
<span class="badge badge-blue">JSON</span>
<span class="badge badge-violet">Builder</span>
<span class="badge badge-green">Active</span>
<span class="badge badge-yellow">Warning</span>
<span class="badge badge-red">Error</span>
<span class="badge badge-gray">Draft</span>
```

### Alerts

```html
<div class="alert alert-info">
  <span class="alert-icon">ℹ️</span>
  This is an info message.
</div>
<div class="alert alert-success">
  <span class="alert-icon">✓</span>
  Operation completed successfully.
</div>
<div class="alert alert-warning">
  <span class="alert-icon">⚠️</span>
  This action cannot be undone.
</div>
<div class="alert alert-danger">
  <span class="alert-icon">✕</span>
  Something went wrong.
</div>
```

### Forms

```html
<div class="form-group">
  <label class="form-label">Field name</label>
  <input type="text" placeholder="Enter value..."/>
  <span class="form-hint">Optional hint text</span>
</div>

<div class="form-group">
  <label class="form-label">Select</label>
  <select>
    <option>Option 1</option>
    <option>Option 2</option>
  </select>
</div>

<div class="form-group">
  <label class="form-label">Textarea</label>
  <textarea placeholder="Enter text..."></textarea>
</div>

<!-- Monospace textarea (for code/JSON) -->
<textarea class="mono" placeholder="Paste JSON here..."></textarea>
```

### Tables

```html
<div class="table-wrap">
  <table>
    <thead>
      <tr>
        <th>Name</th>
        <th>Format</th>
        <th>Status</th>
      </tr>
    </thead>
    <tbody>
      <tr>
        <td class="mono">user-schema-v1</td>
        <td><span class="badge badge-blue">JSON</span></td>
        <td><span class="badge badge-green">Active</span></td>
      </tr>
    </tbody>
  </table>
</div>
```

### Modals

```html
<!-- Trigger -->
<button class="btn btn-primary" onclick="document.getElementById('myModal').classList.add('open')">
  Open Modal
</button>

<!-- Modal -->
<div class="modal-overlay" id="myModal"
     onclick="if(event.target===this) this.classList.remove('open')">
  <div class="modal">
    <div class="modal-title">Modal Title</div>
    <div class="modal-subtitle">Supporting description text.</div>

    <div class="form-group">
      <label class="form-label">Input</label>
      <input type="text" placeholder="Enter value..."/>
    </div>

    <div class="modal-footer">
      <button class="btn btn-ghost"
              onclick="document.getElementById('myModal').classList.remove('open')">
        Cancel
      </button>
      <button class="btn btn-primary">Confirm</button>
    </div>
  </div>
</div>
```

### Status indicators

```html
<div class="status-bar">
  <div class="status-dot ok pulse"></div>
  <span class="status-text ok">Connected to Redis</span>

  <div class="status-dot error" style="margin-left:16px"></div>
  <span class="status-text error">Validation failed</span>
</div>
```

### Pills (format selector)

```html
<div class="flex gap-2">
  <button class="pill active">JSON</button>
  <button class="pill">CSV</button>
  <button class="pill disabled">XML</button>
</div>
```

---

## CSS variables (tokens)

Override any token in your own `<style>` block to customize:

```css
:root {
  --accent:  #2563eb;   /* primary brand color */
  --accent2: #7c3aed;   /* secondary brand color */
  --bg:      #f8faff;   /* page background */
  --text:    #0f172a;   /* primary text */
}
```

Full token reference is in `platform-ui.css` under section 1 (TOKENS).

---

## Layout helpers

```html
<!-- Container -->
<div class="container">max-width 1100px, centered</div>
<div class="container-sm">max-width 720px, centered</div>

<!-- Grids (responsive — collapse to 1 col on mobile) -->
<div class="grid-2"> ... </div>
<div class="grid-3"> ... </div>
<div class="grid-4"> ... </div>

<!-- Flex -->
<div class="flex items-center justify-between gap-4"> ... </div>
```

---

## Favicon

`favicon.svg` is included as a starting point — a blue rounded square with your app initials. Edit the `<text>` content and colors to match your app.

```html
<link rel="icon" type="image/svg+xml" href="/static/favicon.svg"/>
```

---

## Versioning

The version is tracked in a comment at the top of `platform-ui.css`. When updating apps, check the version comment to know what changed.

---

## License

MIT
