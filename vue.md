# 🟢 Vue.js Best Practices

This guide outlines the **best practices** for writing clean, scalable, and maintainable Vue.js (Vue 3 + Composition API) applications.  

---

## 1. Code Structure & Organization
- Use **Composition API** (`setup()`, `ref`, `reactive`, `computed`) instead of Options API for better scalability.
- Organize code into **modules/composables** (`/composables`, `/store`, `/services`).
- Use **`<script setup>`** for cleaner single-file components (SFCs).
- Keep components **small and focused** → each should do **one thing well**.

---

## 2. State Management
- Use **Pinia** instead of Vuex (lighter, TypeScript-friendly).
- Keep **global state** in Pinia stores; use `ref/reactive` for **local state** inside components.
- Use **composables** for reusable stateful logic (e.g., fetching, form handling).

---

## 3. Props & Emits
- Always define **prop types & defaults**.
- Use **`emits` option** to declare events (improves type safety).
- Avoid using `$parent` or `$children`; instead prefer **props/emits** or **provide/inject**.

---

## 4. API & Services
- Keep **API calls** in a dedicated **services layer** (`/services/api.js`) or inside composables.
- Never call APIs **directly in components** unless it’s one-off logic.

---

## 5. Reactivity & Performance
- Use **computed properties** for derived state instead of recalculating in templates.
- Use **watch** only when side-effects are required (not for transformations).
- Use **lazy loading / dynamic imports** for routes & components.
- Use **`v-once`**, **`v-memo`**, or **`keep-alive`** for expensive UI rendering.

---

## 6. Styling
- Prefer **Scoped CSS** inside components to avoid conflicts.
- Use **CSS variables** or **Tailwind CSS** for maintainable design.
- For large projects, consider a **design system** (Vuetify, Naive UI, or custom).

---

## 7. Testing & Linting
- Use **Vue Test Utils + Vitest** (or Jest) for unit testing.
- Use **ESLint + Prettier** for consistent code formatting.
- Enable **TypeScript** for better maintainability in large projects.

---

## 8. Project Structure (Recommended)
```
src/
├── assets/ # Images, fonts, global styles
├── components/ # Reusable UI components
├── composables/ # Reusable logic (useAuth, useFetch, etc.)
├── layouts/ # App layouts
├── pages/ # Page components (Nuxt auto-routes here)
├── services/ # API services (axios/fetch wrappers)
├── store/ # Pinia stores
├── utils/ # Helpers, constants
└── App.vue
```

---

## Summary
- **Organize code** with Composition API, composables, and services.  
- **Manage state** with Pinia and composables.  
- **Optimize performance** with computed, lazy loading, and caching.  
- **Write clean UI** with Scoped CSS or Tailwind.  
- **Ensure quality** with testing, linting, and TypeScript.  

---
