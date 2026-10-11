# Sorrel: a bright neighbourhood pharmacy site with Formgong booking and callback forms

**Live demo:** https://sorrel.formgong.com · Download: the [latest release](https://github.com/formgong/sorrel-template/releases/latest) zip.

[![Deploy to Cloudflare](https://deploy.workers.cloudflare.com/button)](https://deploy.workers.cloudflare.com/?url=https://github.com/formgong/sorrel-template) [![Deploy with Vercel](https://vercel.com/button)](https://vercel.com/new/clone?repository-url=https%3A%2F%2Fgithub.com%2Fformgong%2Fsorrel-template&project-name=sorrel&repository-name=sorrel)

Each button copies the site to your GitHub and publishes it. Then replace `fk_your_access_key` in `index.html` of your copy with your Formgong access key (free at https://formgong.com/new) and commit: the host republishes on its own.

Яскравий сайт незалежної аптеки поруч із домом з формами Формгонг для запису та зворотного дзвінка

A bright, botanical one-page site for an independent pharmacy, in a single `index.html` plus an `img/` folder. The demo pharmacy, Sorrel, its three staff, address, phone, reviews and prices are fictional sample content.

- **Header.** The leaf mark and wordmark on the left, the menu, the phone number and a "Book a jab or check" button. It sticks to the top and gains a shadow once you scroll. On phones it becomes a menu button.
- **Hero.** A split screen: a large serif headline on the left, and on the right a green block where the pharmacist's photo sits in an arch with bold shapes behind it (a raspberry circle, a lime arch, a scored tablet) and hand-drawn sorrel leaves that sway in front. The words of the headline rise in one by one and the shapes roll in.
- **Opening hours panel.** A card hanging from the top of the green block with the hours, phone and address. It says "Open now · until 7 pm" or "Closed · opens tomorrow 8:30 am" from the visitor's clock, and highlights today's row.
- **Delivery check.** Type a postcode and the page answers whether the shop delivers there. The list of areas lives in the script; nothing is sent anywhere.
- **Services.** Five colour-block cards (ask a pharmacist, vaccinations, blood pressure checks, home delivery, skincare and vitamins). On hover a card lifts, its photo zooms and the shape behind it turns. "Book" links pick the matching service in the booking form.
- **Prices.** A dark rounded band with a row per vaccination or check, the price and a Book link.
- **Your visit.** Four steps on the left and a photo on the right. The steps change by themselves every 6 seconds while the section is on screen, with progress bars under the photo. Hover or keyboard focus pauses them; a click jumps to a step.
- **The counter.** A full-width rounded photo of refillable glass jars that slowly zooms out as you scroll, with small outlined tags. Under it, a strip of tilted photos drifts sideways.
- **Team.** Three portraits in arches with a coloured shape behind each, and three short facts.
- **Reviews.** A large 4.9 score and a row of coloured review cards you can scroll or move with the arrow buttons.
- **Questions.** An accordion where the plus turns into a cross.
- **Book or ask.** Two forms side by side: "Book a vaccination or health check" and "Ask a pharmacist" (callback).
- **Footer.** Hours, address, phone, email, and a round back-to-top button that appears once you scroll down.

Blocks fade up as they scroll into view. Without JavaScript everything is visible. With `prefers-reduced-motion: reduce` nothing moves: no sway, no drifting strip, no zoom and no automatic steps.

## English

**Set up the forms**

1. Create a form in the Formgong dashboard and copy its access key. You can use one key for both forms or a separate form for each.
2. In `index.html`, replace both `fk_your_access_key` values with your key.
3. The booking form (`#f-book`) sends `service`, `day`, `time`, `name`, `phone`, `email`, `note`, plus the hidden `subject` ("New booking request from the website") and the `botcheck` spam trap. Name and phone are required; the rest is optional.
4. The callback form (`#f-ask`) sends `name`, `phone`, `call_time`, `question`, plus the hidden `subject` ("Callback request: ask a pharmacist") and `botcheck`. Name and phone are required.
5. Each form shows its thank-you message only when Formgong answers `success: true`. Any other answer shows the error and keeps what was typed.

**Health data.** This form is for appointment requests. Don't use it to collect diagnoses, medical history, prescriptions or insurance numbers; keep those in your clinic's own patient system. Both note fields carry the line "Please don't include medical details here — we'll talk about them in person." There is no prescription upload and no field for medicine names, and the site never promises prescription delivery through a form.

**Edit**

- Colours are at the top of the styles: `--leaf` and `--leaf-d` for the greens, `--beet` for buttons and accents, `--lime`, `--mint` and `--blush` for the shapes and cards, `--ink` for text and dark bands, `--paper` for the page.
- Fonts: Young Serif for headings and Onest for text, both from Google Fonts.
- Opening hours appear in three places: the hero panel, the footer and the `HOURS` object in the script that works out "Open now". Change all three together.
- Delivery areas are the `AREAS` list in the script (postcode districts such as `WM4`).
- Services, prices, steps, staff, reviews and questions are plain HTML; copy a block to add one. A link with `data-pick="Flu vaccination"` selects that service in the booking form, so keep the value the same as the chip's `value`.
- The sorrel leaf is one SVG `<symbol id="leaf">` at the top of the body, reused for the logo, the hero sprig and the decorations. Change its `fill` to recolour a leaf.
- The steps change every 6000 ms (`STEP_MS` in the script).

**Images.** The twelve photos (`hero`, `consult`, `vaccine`, `bp-check`, `delivery`, `counter`, `skincare`, `team-1` to `team-3`, `shop`, `herbs`) were generated for this template with ChatGPT image generation (OpenAI) and saved as WebP; the prompts are in `img-prompts.json`. The people and places are fictional. You may use them in your own site, but replace them with photos of your own pharmacy and team before launch. Until a photo exists, its box shows a flat colour, so the layout never breaks.

**Sample content.** The shop name, staff, address, phone number (a drama-reserved 01632 number), reviews, the 4.9 score and the prices are examples. Replace them with your own before launch.

## Українська

Яскравий односторінковий сайт для незалежної аптеки з ботанічними малюнками. Аптека Sorrel, її працівники, адреса, телефон, відгуки й ціни вигадані.

На сторінці:

- шапка з логотипом-листком, меню, телефоном і кнопкою запису; під час прокрутки вона лишається вгорі й отримує тінь;
- перший екран навпіл: великий заголовок ліворуч, а праворуч зелений блок з фото фармацевтки в арці, яскравими фігурами за нею та намальованими листками щавлю, що гойдаються;
- картка з годинами роботи, яка сама пише «Відчинено, до 19:00» чи «Зачинено» за годинником відвідувача;
- перевірка доставки за поштовим індексом (список районів у скрипті, нічого нікуди не надсилається);
- п'ять кольорових карток послуг, кнопки «Book» обирають потрібну послугу у формі;
- темний блок з цінами на щеплення й перевірки;
- чотири кроки візиту, які перемикаються самі, поки блок на екрані;
- велике фото прилавка з банками, які можна наповнити знову, і стрічка нахилених фото;
- команда з трьох людей, відгуки, питання й відповіді;
- дві форми: запис на щеплення чи перевірку та зворотний дзвінок фармацевта;
- футер з годинами, адресою й контактами.

**Налаштування форм.** Створіть форму в кабінеті Formgong і замініть обидва `fk_your_access_key` у `index.html` на свій ключ. Форма запису надсилає `service`, `day`, `time`, `name`, `phone`, `email`, `note`, форма дзвінка — `name`, `phone`, `call_time`, `question`; в обох обов'язкові ім'я та телефон, а також є приховані `subject` і `botcheck`. Подяка з'являється лише тоді, коли Formgong відповідає `success: true`.

**Медичні дані.** Ця форма лише для запитів на запис. Не збирайте нею діагнози, історію хвороб, рецепти чи номери страховок; зберігайте їх у власній системі пацієнтів аптеки чи клініки. Біля полів для коментаря є попередження не писати медичних подробиць. Завантаження рецептів і поля для назв ліків немає.

**Редагування.** Кольори — змінні вгорі стилів (`--leaf`, `--beet`, `--lime` та інші). Години роботи записані у трьох місцях: картка на першому екрані, футер і об'єкт `HOURS` у скрипті, тож міняйте їх разом. Райони доставки — список `AREAS` у скрипті.

**Зображення:** дванадцять фото згенеровано для цього шаблону в ChatGPT (OpenAI) і збережено у WebP; промпти лежать у `img-prompts.json`. Люди й місця вигадані. Їх можна використовувати, але перед запуском замініть їх фото своєї аптеки й команди.

**Приклади.** Назва, працівники, адреса, телефон, відгуки, оцінка 4.9 і ціни — це приклади, замініть їх своїми.

MIT license.
