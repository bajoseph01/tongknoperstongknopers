# Afrikaanse Tongknopers

An interactive, single-file classroom web app for practising Afrikaans tongue twisters with Grade 4–6 First Additional Language learners.

Live app: https://bajoseph01.github.io/tongknoperstongknopers/

---

## What this app is

This app is a small classroom tool for teaching Afrikaans pronunciation, rhythm, listening accuracy, and vocabulary through **tongknopers** — Afrikaans tongue twisters.

Learners do not see every sentence immediately. Each card starts blurred, so the teacher can pace the activity and create curiosity. When a card is clicked for the first time, the Afrikaans tongue twister is revealed. After that, clicking the same card toggles between the Afrikaans sentence and its English meaning.

The design is intentionally playful but still classroom-friendly: it uses a **notebook-doodle style**, lined-paper background, chunky card borders, and simple teacher controls.

---

## Who it is for

This was designed for:

- Grade 4–6 Afrikaans FAL learners
- second-language Afrikaans classrooms
- oral fluency warm-ups
- pronunciation practice
- vocabulary retrieval
- fun end-of-lesson challenges
- teacher-led interactive whiteboard use

It can also work well as a quick station activity, pair challenge, or revision tool.

---

## Classroom learning goals

The app supports several useful language-learning moves:

### 1. Pronunciation practice

Tongue twisters help learners practise repeated sound patterns such as:

- **k** as in `Klein Koos kook koue kos`
- **p** as in `Pieter pluk pers perskes`
- **s** as in `Sannie sê sy sal sewe sakke sout sleep`
- **r** as in `Rooi rose ruik regtig rond`
- **v/f** as in `Vlok vlieg vinnig verby vyf vriende`

### 2. Retrieval before reveal

The blurred-card design creates a small prediction moment. Learners can try to remember, guess, or anticipate before the teacher reveals the card.

### 3. Meaning check

The Afrikaans ↔ English toggle helps learners check meaning without turning the activity into a long translation lesson.

### 4. Focused attention

Tabs split the material into levels so learners are not overloaded by too many sentences at once.

### 5. Fluency through repetition

The teacher routine is simple:

1. Say it slowly and clearly.
2. Say it at normal speed.
3. Say it faster without losing accuracy.

Speed comes last. Clean pronunciation comes first.

---

## Main features

- **Single HTML file**: everything is inside `index.html`
- **No external libraries**: no build tools, no React, no package installation
- **GitHub Pages-ready**: can be hosted directly from the repository root
- **Notebook-doodle design**: friendly, hand-drawn classroom feel
- **Level tabs**:
  - `Maklik`
  - `Gemiddeld`
  - `Uitdaging`
- **Blurred card reveal**: cards are hidden until first clicked
- **Bilingual toggle**: after reveal, cards switch between Afrikaans and English
- **Random challenge button**: chooses one card for the class
- **Show all levels button**: reveals all level sections when needed
- **Print-friendly mode**: printing removes unnecessary controls and shows the content clearly
- **Keyboard accessible**: cards can be activated with Enter or Space, and tabs can be changed with arrow keys

---

## How the app was put together

The app was built as a **single self-contained web page** using three standard web technologies:

### 1. HTML

The HTML provides the structure of the app:

- a page wrapper
- title and teacher note
- tab buttons
- control buttons
- three level sections
- individual tongue-twister cards
- a short classroom routine section

Each tongue-twister card stores two versions of the sentence:

```html
data-phrase="Pieter pluk pers perskes."
data-english="Pieter picks purple peaches."
```

This allows the JavaScript to switch between the Afrikaans and English versions without needing a database or extra file.

---

### 2. CSS

The CSS creates the visual design:

- lined notebook-paper background
- red margin line
- chunky black doodle-style borders
- soft classroom colours
- card shadows
- blurred locked cards
- responsive layout for different screen sizes
- print styling

The card reveal effect is handled mainly through CSS classes:

```css
.card.locked { ... }
.card.translated { ... }
```

A locked card is blurred and covered with a “Klik om te onthul” label. A translated card changes its look slightly and displays the English version.

---

### 3. JavaScript

The JavaScript controls the interaction:

- locking all cards when the page loads
- revealing a card on first click
- toggling Afrikaans ↔ English after reveal
- switching between level tabs
- showing all levels
- choosing a random class challenge
- supporting keyboard interaction

The main teaching interaction is:

```js
if (card.classList.contains('locked')) {
  card.classList.remove('locked');
  phrase.textContent = card.dataset.phrase;
  return;
}

const isEnglish = card.classList.toggle('translated');
phrase.textContent = isEnglish ? card.dataset.english : card.dataset.phrase;
```

This keeps the classroom flow simple:

1. locked card
2. reveal Afrikaans
3. toggle English meaning
4. toggle back to Afrikaans

---

## Suggested classroom flow

### Warm-up version: 5 minutes

1. Open the app on the board.
2. Choose `Maklik`.
3. Click one card.
4. Learners repeat after the teacher.
5. Learners try it with a partner.
6. Class tries it faster together.

### Challenge version: 10 minutes

1. Click `Kies een vir die klas`.
2. Reveal the selected tongue twister.
3. Learners practise in pairs.
4. Volunteers try it aloud.
5. Click for English meaning only after pronunciation practice.

### Revision version: 15 minutes

1. Use all three levels.
2. Ask learners to predict meanings before toggling English.
3. Pick 8–10 vocabulary words for spelling, translation, or crossword practice.

---

## Vocabulary extension ideas

Useful words from the tongue twisters for vocabulary or crossword work include:

| Afrikaans | English |
|---|---|
| koue | cold |
| kos | food |
| perskes | peaches |
| kat | cat |
| krat | crate |
| sakke | bags |
| sout | salt |
| muffins | muffins |
| rose | roses |
| gate | holes |
| vriende | friends |
| brood | bread |
| slak | snail |
| druiwe | grapes |
| varke | pigs |
| tamaties | tomatoes |
| tuinmuur | garden wall |
| rotse | rocks |

---

## File structure

```text
tongknoperstongknopers/
├── index.html   # full interactive app
└── README.md    # project explanation and usage notes
```

---

## How to edit the app

To add another tongue twister, copy one of the existing card blocks in `index.html` and change:

- `data-phrase`
- `data-english`
- the visible sentence inside `<p class="phrase">...</p>`
- the sound badge, for example `R-klank`, `S-klank`, or `V-klank`

Example:

```html
<article class="card" data-phrase="Nuwe sin hier." data-english="English meaning here." tabindex="0" role="button" aria-label="Klik om die tongknoper te onthul">
  <span class="badge">16 · N-klank</span>
  <p class="phrase">Nuwe sin hier.</p>
  <div class="hint"><span class="chip sound">n</span><span class="chip level">nuut</span></div>
</article>
```

---

## Deployment notes

This app is deployed with GitHub Pages.

Recommended GitHub Pages settings:

- **Source**: Deploy from a branch
- **Branch**: `main`
- **Folder**: `/root`

Because the app is a plain `index.html` file in the repository root, GitHub Pages can serve it directly.

---

## Design philosophy

The app was designed around a simple teaching principle:

> Reduce visual overload, create one clear focus point, and make learners retrieve or predict before revealing support.

That is why the app uses:

- tabs instead of one long page
- blurred cards instead of all answers showing immediately
- one-click reveal
- bilingual toggling only after the Afrikaans sentence has been seen
- a random challenge button for retrieval-style practice

The goal is not just a pretty web page. The goal is a stronger classroom learning loop:

**predict → reveal → practise → check meaning → repeat**
