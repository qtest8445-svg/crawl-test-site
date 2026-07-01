# 🕷 Crawl Test Site

Тестовий сайт для перевірки режимів краулінгу URL у [all2wiki.com portal](https://portal.all2wiki.com/).

## Структура сайту

Сайт має **5 рівнів вкладеності** з 24 сторінками, рівномірно розподіленими по 4 секціях.

```
index.html                                        ← depth 0 (root)
├── about/index.html                              ← depth 1
│   ├── about/team.html                           ← depth 2
│   │   ├── about/members/alice.html              ← depth 3
│   │   └── about/members/bob.html                ← depth 3
│   └── about/history.html                        ← depth 2
├── products/index.html                           ← depth 1
│   └── products/category/index.html              ← depth 2
│       ├── products/category/clothing.html       ← depth 2
│       └── products/category/item/laptop.html    ← depth 3
│           ├── products/category/item/specs.html ← depth 4
│           │   └── .../deep-review.html          ← depth 5
│           └── products/category/item/reviews.html ← depth 4
├── blog/index.html                               ← depth 1
│   ├── blog/post/intro.html                      ← depth 2
│   │   └── blog/post/comments/thread1.html       ← depth 3
│   │       └── blog/post/comments/reply1.html    ← depth 4
│   └── blog/post/guide.html                      ← depth 2
└── docs/index.html                               ← depth 1
    ├── docs/quickstart.html                      ← depth 2
    └── docs/api/index.html                       ← depth 2
        ├── docs/api/v2.html                      ← depth 3
        └── docs/api/v1/index.html                ← depth 3
            ├── docs/api/v1/endpoints/users.html  ← depth 4
            │   └── .../users-detail.html         ← depth 5
            └── docs/api/v1/endpoints/auth.html   ← depth 4
```

## Покриття по режимах

| Режим | Опис | Сторінок |
|---|---|---|
| `single` | Тільки стартова сторінка | **1** |
| `depth_1` | Root + прямі посилання | **5** |
| `depth_2` | + ще один рівень *(default)* | **11** |
| `depth_3` | | **16** |
| `depth_4` | | **21** |
| `depth_5` | | **24** |
| `full_site` | Весь сайт | **24** |

> 📋 Повна таблиця покриття: [`crawl-map.html`](./crawl-map.html)

## Як використовувати

1. Відкрий [portal.all2wiki.com](https://portal.all2wiki.com/)
2. Встав URL цього сайту в поле **"OR ENTER A URL"**:
   ```
   https://<your-username>.github.io/crawl-test-site/
   ```
3. Вибери **URL CRAWL SCOPE** який хочеш перевірити
4. Порівняй кількість проіндексованих сторінок з таблицею вище

## Як читати кожну сторінку

Кожна HTML-сторінка містить:
- 🏷 **SECTION badge** — шлях секції
- 🟢 **DEPTH badge** — глибина від кореня
- ℹ️ **Info block** — при яких режимах буде/не буде проіндексована
- 🔗 Навігацію вгору і вниз по дереву
