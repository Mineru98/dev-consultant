# SPA Tech Stack Guide

Reference for client-side technology decisions.

## Framework Selection

### Vanilla JavaScript (Default)
**Use when:**
- Simple to medium complexity apps
- No build step required
- Maximum browser compatibility
- Learning/prototyping

**Pros:**
- Zero dependencies
- No build process
- Full control
- Smaller bundle size

**Cons:**
- More boilerplate
- Manual state management
- No component system

### When to Consider Frameworks
If requirements include:
- Complex state management
- Server-side rendering
- Large team collaboration
- Extensive testing needs

→ Recommend user evaluate React/Vue/Svelte separately

## Storage Solutions

### LocalStorage
**Best for:**
- Settings and preferences
- Session state
- Small key-value data
- < 5MB total

```javascript
// Read
const theme = localStorage.getItem('theme') || 'light'

// Write
localStorage.setItem('theme', 'dark')

// Delete
localStorage.removeItem('theme')

// Clear all
localStorage.clear()
```

**Limits:**
- ~5MB per origin
- Strings only (JSON.stringify needed)
- Synchronous API
- No indexing/querying

### IndexedDB (via localbase)
**Best for:**
- User-generated content
- Large datasets (> 5MB)
- Complex data structures
- Blob/file storage
- Structured queries

**Limits:**
- ~50MB typical (browser varies)
- Async only
- No SQL (client-side filtering)
- Single-user (no sync)

### Selection Matrix

| Requirement | LocalStorage | IndexedDB |
|-------------|--------------|-----------|
| Settings/Preferences | ✅ | ❌ |
| User Data (< 100 items) | ⚠️ | ✅ |
| User Data (> 100 items) | ❌ | ✅ |
| File/Image Storage | ❌ | ✅ |
| Offline Support | ✅ | ✅ |
| Complex Queries | ❌ | ⚠️ |

## Routing Patterns

### Hash-Based Routing
```javascript
// URL: example.com/#/page
window.addEventListener('hashchange', () => {
  const route = location.hash.slice(1) || '/'
  renderPage(route)
})
```

**Pros:** Simple, no server config needed
**Cons:** Less clean URLs

### History API Routing
```javascript
// URL: example.com/page
function navigate(path) {
  history.pushState({}, '', path)
  renderPage(path)
}

window.addEventListener('popstate', () => {
  renderPage(location.pathname)
})
```

**Pros:** Clean URLs
**Cons:** Requires server config for refresh

### Recommendation
Use **hash-based routing** for client-only apps (no server needed).

## State Management

### Simple State (Vanilla)
```javascript
const state = {
  data: [],
  loading: false,
  error: null
}

function setState(updates) {
  Object.assign(state, updates)
  render()
}
```

### Event-Based State
```javascript
const store = {
  state: { count: 0 },
  listeners: [],

  subscribe(fn) {
    this.listeners.push(fn)
  },

  dispatch(action) {
    this.state = reducer(this.state, action)
    this.listeners.forEach(fn => fn(this.state))
  }
}
```

### Recommendation
- Simple apps: Direct state object
- Medium apps: Event-based store
- Complex apps: Consider framework

## Build Tools

### No Build (Default)
```html
<!-- Direct script inclusion -->
<script src="https://cdn.tailwindcss.com"></script>
<script type="module" src="app.js"></script>
```

**Pros:** Zero config, instant reload
**Cons:** No minification, no bundling

### Vite (If Build Needed)
```bash
npm create vite@latest my-app -- --template vanilla
```

**Use when:**
- Multiple JS files needing bundling
- CSS/JS minification required
- Environment variables needed
- Production optimization needed

## CSS Strategy

### Tailwind CDN (Default)
```html
<script src="https://cdn.tailwindcss.com"></script>
```

**Pros:** Zero setup, full utility classes
**Cons:** Larger file, no custom config

### Tailwind CLI (Production)
```bash
npx tailwindcss -i input.css -o output.css --minify
```

**Use when:** Production deployment, custom theme needed

## Search Prompts for Research

When researching client-side solutions:

```
"[technology] vanilla JavaScript implementation 2024"
"[feature] client-side only no backend"
"[library] CDN browser usage"
"IndexedDB vs LocalStorage [use case]"
"[pattern] without framework pure JS"
```

## Common Patterns Reference

### Fetch with Error Handling
```javascript
async function fetchData(url) {
  try {
    const res = await fetch(url)
    if (!res.ok) throw new Error(`HTTP ${res.status}`)
    return await res.json()
  } catch (error) {
    console.error('Fetch failed:', error)
    return null
  }
}
```

### Debounce
```javascript
function debounce(fn, ms = 300) {
  let timeout
  return (...args) => {
    clearTimeout(timeout)
    timeout = setTimeout(() => fn(...args), ms)
  }
}
```

### Local Date Formatting
```javascript
function formatDate(isoString) {
  return new Date(isoString).toLocaleDateString('ko-KR', {
    year: 'numeric',
    month: 'long',
    day: 'numeric'
  })
}
```

## Technology Decision Template

```markdown
## Decision: [Topic]

### Options Evaluated
1. [Option A]: [brief description]
2. [Option B]: [brief description]

### Selection: [Chosen Option]

### Rationale
- [Reason 1]
- [Reason 2]

### Trade-offs Accepted
- [Trade-off 1]
```
