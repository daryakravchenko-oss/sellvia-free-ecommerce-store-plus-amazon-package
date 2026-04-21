# Sellvia — Free Ecommerce Store + Amazon Package

Лендинг для клиентов Sellvia. Одностраничный сайт: бесплатный онлайн-магазин + Amazon Seller Kit бонус.

## 🗂 Проект

- **Локальная папка:** `D:\Work\sellvia-free-ecommerce-store-plus-amazon-package\`
- **GitHub:** https://github.com/daryakravchenko-oss/sellvia-free-ecommerce-store-plus-amazon-package
- **Стартовая страница:** `file:///D:/Work/sellvia-free-ecommerce-store-plus-amazon-package/index.html`
- **Происхождение:** клон с `https://sellvia.com/custom-store/` (~апрель 2026)

## 📁 Структура

```
├── index.html        # Единый файл: HTML + inline CSS + inline JS (~120 KB)
├── img/
│   ├── Hero/         # 4 слайда hero (2158, 2161, 2162, 2163.webp)
│   ├── Awards/       # 3 логотипа наград
│   ├── Bonus/        # 8 фото бонус-секции (2119–2149, аватарки)
│   ├── featured/     # 6 SVG медиа (Forbes, Inc, NBC, Fox, Business.com, Entrepreneur)
│   ├── icons/        # 9 vuesax/linear SVG иконок
│   ├── products/     # 10 обложек продуктов (ebook/курсы)
│   ├── ratings/      # 4 логотипа платформ отзывов (Sitejabber, Trustpilot, G2, Facebook)
│   ├── reviews/      # 6 постеров видео-отзывов (ruby, christina, rodney, jack, ksenia, miandra)
│   └── stores/       # 6 скринов дизайнов магазинов (хедеры/каталоги)
└── CONTEXT.md        # Этот файл
```

**Видео-отзывы:** подгружаются с `https://sellvia.com/wp-content/uploads/reviews/*.mp4` (6 файлов, не хранятся локально).

## 🧩 Структура страницы (секции сверху вниз)

1. **Topbar** — оранжевый градиент, "Special Offer" badge + CTA → checkout
2. **Nav** — чёрный sticky, логотип Sellvia + ссылки (Why Sellvia / What's included / Bonus / FAQ) + amber кнопка "Start for free" (38px pill)
3. **Hero** — чёрный, 4-слайдный slideshow с затемнением, заголовок "Start your online business for FREE today", CTA-кнопка
4. **Stat bar** — 3 счётчика с count-up анимацией (1,500,000+ / $1.5B+ / 4.8★)
5. **Awards** — 3 белые карточки с логотипами наград (Hermes Gold / MarCom Platinum / dotCOMM Gold)
6. **Ratings** — тёмный блок, 4 платформы отзывов + FEATURED ON marquee-слайдер с логотипами медиа
7. **Why Sellvia** — светлый фон, "Everything you need. Nothing you don't.", 3 карточки с иконками
8. **What will I sell?** (sell-sec) — чёрный, бесшовный горизонтальный слайдер 10 продуктов с drag-to-scroll
9. **How it works** (how-sec) — светлый фон, 3 шага (01/02/03) "From zero to sale in 3 simple steps"
10. **What do I get for free?** (get-sec) — чёрный, 6 карточек с Figma-иконками (shop/designtools/shopping-bag/card/profile-tick/24-support), эффект glow-orb следует за курсором
11. **Bonus — Amazon Seller Kit** — светлый блок с пилюлей `BONUS · ~~$399~~ → FREE` (анимированная SVG-обводка), 3 интерактивных буллета + правая панель с фото и glass-карточками (Brownian motion)
12. **Store Designs marquee** — чёрный, "What will my store look like?", горизонтальный бесшовный слайдер 6 дизайнов магазинов с drag-to-scroll
13. **Testimonials (test-sec)** — светлый, "1,500,000+ store owners", 6 видео-карточек с постерами и click-to-play
14. **FAQ** — чёрный, 9 вопросов-аккордеонов + sticky CTA-сайдбар с live social proof counter
15. **Final CTA** — "Your store is waiting for you.", radial amber glow, CTA-кнопка
16. **Footer** — минималистичный (copyright + privacy policy)
17. **Sticky CTA** — fixed bottom на всех экранах

## 🎨 Дизайн-система

**Шрифт:** `-apple-system, BlinkMacSystemFont, "SF Pro Display", "Helvetica Neue"`

**Цвета:**
```css
--c-amber:    #f5a623   /* Главный акцент Sellvia */
--c-amber-d:  #d4891a   /* Hover */
--c-black:    #000000
--c-near:     #1d1d1f   /* Почти чёрный */
--c-lightbg:  #f5f5f7   /* Apple светлый фон */
--c-gray2:    #6e6e73   /* Основной серый текст */
```

**Кнопки:**
- `.btn-filled` — **358px × 60px**, amber, pill (border-radius: 980px), font-size 19px
- Nav `.nav-signup` — pill 38px, 14px шрифт, 16px padding
- Hover: `transform: scale(1.02)` + `will-change: transform` (защита от subpixel-дёрганья)

**Breakpoints (mobile):**
- `≤1200px`: padding 100px
- `≤860px`: padding 72px
- `≤600px`: некоторые элементы меняют компоновку
- `≤480px`: padding 56px 16px
- `≤375px`: iPhone X/SE — padding 48px 14px, шрифты мельче
- `≤360px`: Galaxy S8–S21 — padding 44px 12px
- `≤320px`: iPhone SE 1 — padding 40px 10px

## ⚙️ Ключевые технические решения

- **Единый файл** — весь CSS и JS инлайн, никаких внешних файлов кроме картинок и видео
- **JS-driven marquees** через `requestAnimationFrame` (не CSS animation) — это позволяет drag-to-scroll
- **Видео без нативных контролов** — `controls: false`, клик на видео = play/pause
- **Bonus pill обводка** — SVG `<rect>` с `stroke-dasharray` и JS-вычислением периметра для идеальной pill-формы на разной ширине
- **Glow orb в Included** — `radial-gradient` с `object-fit: cover` + mouse tracking + touch support
- **Brownian motion** — Ornstein-Uhlenbeck процесс для плавного дрожания glass-карточек в bonus-секции
- **Scroll reveal** — IntersectionObserver с `.appear` классами и delay `.d1`, `.d2` ...
- **FAQ accordion +/×** — CSS pseudo-элементы (2 линии) для идеального центрирования, `rotate(45deg)` при открытии
- **Overflow hidden** — `html { overflow-x: hidden }` + max-width на всех marquee-контейнерах (предотвращает правый сдвиг на мобиле)

## 🧠 Память Claude (что знает в новом диалоге)

### Auto-memory (всегда доступно)
- **Figma Icon Library** — `MEMORY.md` → `reference_figma_icons.md`
  - 928 vuesax/linear иконок, file key `YyOJv1gUSBiIE3Y7OSNoyq`

### Skills (вызывать через Skill tool)
- **`sellvia-knowledge`** — полная база знаний о Sellvia (company-profile, customer-profile, customer-journey, product-bible). Использовать при любой работе с Sellvia контентом/дизайном
- **`icons`** — Figma иконки, node IDs для популярных иконок
- **`docx`**, **`pdf`**, **`xlsx`**, **`pptx`** — работа с документами (интервью клиентов уже лежат в `C:\Users\PC\Downloads\`)

### Terminology правила Sellvia (КРИТИЧНО)
| ❌ Никогда не использовать | ✅ Вместо этого |
|---|---|
| Dropshipping | Online business / Online store |
| Digital products | Products / Things to sell |
| Passive income | (Никогда не использовать) |
| Get rich quick | (Никогда не использовать) |
| Warehouse / Shipping | (Не релевантно) |

## 🎬 Видео-отзывы (URL на sellvia.com)

- **Ruby** — `ruby_review%20(1080p).mp4` — "First sale within 2 weeks"
- **Christina** — `christina_review%20(1080p).mp4` — "Turned $500 into a 6-figure business"
- **Rodney** — `rodney_review_2_(1080p).mp4` — "$10K in 28 days with 2 stores"
- **Jack** — `jack_review%20(1080p).mp4` — "Single dad turned ecommerce entrepreneur"
- **Ksenia** — `ksenia_review%20(1080p).mp4` — "$2,700 in 3 months as a new mom"
- **Miandra** — `miandra_review%20(1080p).mp4` — "From burnout to freedom in 6 weeks"

## 🚀 Быстрый старт для нового диалога

```bash
# Локальная работа
cd "D:\Work\sellvia-free-ecommerce-store-plus-amazon-package"
# Открыть в браузере
file:///D:/Work/sellvia-free-ecommerce-store-plus-amazon-package/index.html

# Git
git status
git pull
git add . && git commit -m "..." && git push
```

**Для полного контекста в новом диалоге — сначала прочитай этот CONTEXT.md и вызови Skill `sellvia-knowledge`.**
