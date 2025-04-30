# VocaBoost

**VocaBoost** is an AI-powered platform built by **Suresh Jatavath** to help users improve their speaking skills. By analyzing both speech and facial expressions, VocaBoost generates suggestions that help users to improve their speeches.

Using modern technologies like LLMs and face detection, it evaluates and enhances your speech across three key dimensions:

- **Emotion** – Finds sentences where the speaker’s emotions could be improved to make the speech more engaging.
- **Clarity** – Highlights areas where the speech could be clearer and provides suggestions for improvement.
- **Relevance** – Points out sections that are off-topic or unnecessary.

VocaBoost is a great platform to practice and refine your speeches before delivering them.

---

## 📁 Monorepo Structure (Turborepo)

```
apps/
├── frontend         # Next.js + TailwindCSS + Jotai + face-api.js
├── backend          # Express.js + LangChain + Prisma + PostgreSQL
└── backend-cache    # Express.js + Bloom filters for fast checks
```

---

## 🚀 Features

- 🧑‍💻 Record your speech and facial expressions
- 🤖 Analyze speech using an LLM (via LangChain + Google Gemini)
- 🧍 Emotion detection from facial expressions (via `face-api.js`)
- 🧠 Smart feedback on speech emotion, clarity, and relevance
- ⚡ Quick username and email availability check using Bloom Filters (fast but there is a small chance of false positives).
- 🧹 Code and Commit quality enforced using ESLint, Commitlint, Husky, and `lint-staged`

---

## 🧪 Bloom Filter Optimization

**Bloom Filters** are used in the `backend-cache` microservice to:

- ✅ Quickly check if a **username or email** likely exists
- 🧠 Reduce unnecessary **PostgreSQL queries**
- ⚡ Improve **signup performance** under heavy load
- ✅ Ensure **no false negatives** (but tolerate rare false positives)

Ideal for scalable applications where fast existence checks are required.

---

## ⚙️ Tech Stack

### Frontend (`apps/frontend`)
- **Framework**: Next.js 15
- **UI**: Tailwind CSS 4, `clsx`, `tailwind-merge`
- **State**: `jotai`
- **Face Detection**: `face-api.js`
- **Animations**: `motion`
- **Lang**: TypeScript 5

### Backend (`apps/backend`)
- **Server**: Express 5
- **LLM**: LangChain + Google Gemini
- **Auth & Security**: JWT, bcrypt, helmet, zod
- **Database**: PostgreSQL via Prisma
- **Dev Tools**: ts-node-dev, nodemon

### Backend Cache (`apps/backend-cache`)
- **Server**: Express 5  
- **Cache Mechanism**: Bloom Filters (via `bloom-filters`) for fast existence checks  
- **Validation & Security**: Zod, Helmet, CORS  
- **Dev Tools**: TypeScript, ts-node, nodemon

---

## 🔍 Linting, Formatting & Commits

### ✅ ESLint Rules

Eslint rules are added, like:
- No unused variables or expressions
- No `else` after `return`
- Always use semicolons
- Functions must have consistent return behavior
- Maximum of 4 parameters per function
- No trailing spaces
- 2-space indentation
- Double quotes preferred

### `lint-staged` + Husky

- Ensures only **staged files** are linted before commit.
- Prevent bad commits while keeping workflow fast.

### Husky Hooks

- `pre-commit`: Runs `npm run build` and `npx lint-staged`
- `commit-msg`: Uses `commitlint` npm package to enforce conventional commit messages

---

## 📦 Database

- **PostgreSQL**
- ORM: **Prisma** with **Accelerate extension** for optimized performance

```bash
# Run migrations
npx prisma migrate dev

# Generate client
npx prisma generate --no-engine
```

---

## 🧪 Development

### Prerequisites

- Node.js ≥ 18
- PostgreSQL
- Turbo CLI: `npm install -g turbo`

### Setup

```bash
git clone https://github.com/Snnayak111/VocaBoost.git
cd VocaBoost
npm install
```

After installing dependencies, run the following command in the apps/backend/prisma folder to generate the Prisma client:

```
npx prisma generate --no-engine
```

---

Sure! Here's the updated section to include that **VocaBoost works only in Chrome browser**:

---

## ⚠️ Browser Compatibility

> **Note:** VocaBoost currently supports **only the Chrome browser** 

---

## 📌 Root-level Scripts

```bash
# Start all apps in development mode
npm run dev

# Build all apps
npm run build

# Run the production build
npm run start

# Lint all apps
npm run lint

# Auto-fix some linting issues in all apps
npm run lint:fix

# Format codebase using Prettier
npm run format

```

---

## 🤝 Contributing

Feel free to fork and contribute! Make sure to follow lint and commit rules before submitting a pull request.