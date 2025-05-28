# QuietNews: A Privacy-Focused News Aggregator

Welcome to **QuietNews**, a Next.js application designed as a take-home assignment for frontend engineer positions. This README serves as both the project overview and the technical design document, guiding you through the implementation and demonstrating best practices with Next.js v15.

---

## 📝 Technical Design

### 1. Project Structure

```
/ (root)
├── components/        # Reusable UI components (SearchBar, ArticleCard, FilterMenu, Layout)
├── pages/
│   ├── index.js       # Homepage with search bar and popular articles
│   ├── search/        # Search results pages
│   │   └── index.js   # Handles ?q= and &category=
│   └── article/       # Article detail pages
│       └── [id].js    # Dynamic route for article content
├── public/            # Static assets (favicon, icons)
├── styles/            # Global styles and Tailwind config
├── utils/             # Helper functions (API clients, formatters)
└── docs/              # Additional documentation (if needed)
```

### 2. Data Fetching Strategy

* **Homepage**: `getStaticProps` to fetch top articles at build time for performance and caching.
* **Search Results**: `getServerSideProps` to handle query parameters and return real-time search results.
* **Article Detail**: `getStaticPaths` + `getStaticProps` for top N articles, fallback: 'blocking' for new ones.
* **Client Components**: Use `fetch` inside server components or server actions for user-driven filters.

### 3. Routing & Navigation

* **Dynamic Routing**: `/article/[id]` for individual articles.
* **Query Params**: `/search?q=keyword&category=tech` parsed in `getServerSideProps`.
* **Navigation**: `next/link` for prefetching, `useRouter` for reading URL state.

### 4. State Management

* **URL as Source of Truth**: All search state (terms, filters) lives in query parameters.
* **Local UI State**: Component-level state for dropdown open/close, theme toggle, loading indicators.
* **Global State**: Minimal; theme stored in `Context` with server component + client provider.

### 5. Performance Considerations

* **Server Components**: Default for page layout and data-fetching to minimize client bundle size.
* **Lazy Loading**: `next/image` for images, dynamic import for non-critical components.
* **Caching**: ISR (Incremental Static Regeneration) for article pages, HTTP caching headers.
* **Loading UI**: Suspense + fallback spinners for slow network.

### 6. Accessibility & UX

* **Keyboard Navigation**: Focus states on buttons/links, skip-to-content link.
* **ARIA Roles**: `role="search"`, `aria-label`, and proper heading hierarchy.
* **Feedback**: Form validation, loading states, and error messages.

### 7. SEO Strategy

* **Head Metadata**: `next/head` with dynamic `<title>`, `<meta name="description">`, Open Graph tags.
* **Structured Data**: JSON-LD for articles.

---

## 🛠 Implementation Requirements

* **Framework**: Next.js v15
* **Styling**: Tailwind CSS
* **State Libraries**: No external state libs (e.g., Redux, Zustand)
* **Linting & Formatting**: ESLint + Prettier
* **Deployment**: Deploy on Vercel (optional but preferred)

### Functional Checklist

* [ ] Homepage with search bar and popular articles
* [ ] Search results page with filters and URL sync
* [ ] Article detail page with full content
* [ ] Responsive design across devices
* [ ] Performance optimizations (SSR/ISR, lazy loading)
* [ ] Accessibility features (ARIA, keyboard nav)
* [ ] SEO enhancements (metadata, JSON-LD)

### Bonus Features

* [ ] Light/dark mode toggle
* [ ] Pagination or infinite scroll on results
* [ ] Offline support (PWA)

---

## 🚀 Getting Started

1. **Clone the repo**:

   ```bash
   git clone https://github.com/your-username/quietnews.git
   cd quietnews
   ```
2. **Install dependencies**:

   ```bash
   npm install
   ```
3. **Run in development**:

   ```bash
   npm run dev
   ```
4. **Build for production**:

   ```bash
   npm run build
   npm start
   ```

---

## 📂 Submission

* Ensure your **design document** is clear (this README).
* Push your code to a **GitHub repository** with a descriptive README.
* (Optional) Deploy on **Vercel** and include the live link.
* Comment on **time taken** and **future improvements** in your repo's issues or PR description.

---

*By completing this assignment, you'll demonstrate your mastery of Next.js v15 features, performance best practices, and user-centric design.*
