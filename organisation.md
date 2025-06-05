🗂️ Struktura katalogów projektu (SvelteKit Allegro Clone)
src/
│
├── routes/
│   ├── +layout.svelte             # Layout główny z nav/footer
│   ├── +page.svelte               # Strona główna z promowanymi produktami
│   ├── login/+page.svelte         # Logowanie
│   ├── register/+page.svelte      # Rejestracja
│   ├── products/
│   │   ├── +page.svelte           # Lista produktów z filtrami/sortowaniem
│   │   └── [id]/+page.svelte      # Szczegóły produktu
│   ├── cart/+page.svelte          # Koszyk
│   ├── orders/+page.svelte        # Historia zamówień użytkownika
│   └── dashboard/                 # Panel sprzedawcy
│       ├── +layout.svelte
│       ├── products/+page.svelte  # Twoje produkty
│       └── orders/+page.svelte    # Zamówienia klientów
│
├── lib/
│   ├── components/                # Nav, ProductCard, Modal itp.
│   ├── stores/                    # Koszyk, auth, theme
│   ├── utils/                     # Formatowanie cen, walidacje, helpery
│   └── api/                       # Fetchery do endpointów API
│
├── styles/                        # Tailwind config / global CSS
├── hooks.server.ts                # Hooki serwerowe np. auth, cookies
└── app.d.ts                       # Typowanie globalne (np. User, Session)
