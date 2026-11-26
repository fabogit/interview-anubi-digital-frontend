# interview-anubi-digital-frontend

> A Next.js 12 and React 17 server-side rendered (SSR) web application featuring Tailwind CSS styling, Axios data fetching, and tabular cryptocurrency ledger presentation.

**Inception (First Commit):** `2022-05-13` • **Batch / Horizon:** `batch-2021-2022` • **Architecture Domain:** `Frontend Architecture / Next.js Client`

---

## 📌 Architecture & Overview

`JobInterview_anubi-frontend` is the client-facing presentation layer developed for the Anubi Digital recruitment assessment. It interfaces with the backend service [`interview-anubi-digital-backend`](https://github.com/fabogit/interview-anubi-digital-backend) to render historical cryptocurrency transaction ledgers via Next.js Server-Side Rendering (`getServerSideProps`).

The user interface leverages Tailwind CSS utility classes and Next.js CSS Modules to render responsive, styled tabular records detailing transaction timestamps, user IDs, amounts, nature codes, and asset types.

```
+-------------------------------------------------------------------------+
|                       JobInterview_anubi-frontend                       |
|                                                                         |
|  [ Browser User ]                                                       |
|         |                                                               |
|         | HTTP GET /                                                    |
|         v                                                               |
|  +--------------------+       HTTP GET /v1/transactions                 |
|  | pages/index.tsx    +----------------------------------------+        |
|  | (getServerSideProps)                                        |        |
|  +---------+----------+                                        |        |
|            |                                                   v        |
|            | Injects { props: { data } }       +----------------------+ |
|            v                                   | JobInterview_anubi-  | |
|  +--------------------+                        | backend (Port: 3081) | |
|  | React SSR Table    |                        +----------------------+ |
|  | (Tailwind CSS)     |                                                 |
|  +--------------------+                                                 |
+-------------------------------------------------------------------------+
```

* **Context:** Technical interview frontend application for Anubi Digital, designed to demonstrate Next.js SSR lifecycles, Axios integration, and modern CSS utility design.
* **Key Patterns:**
  * **Server-Side Rendering (SSR):** Data pre-fetching on every incoming request inside `getServerSideProps` to ensure immediate HTML rendering.
  * **Paired Client-Server Contract:** Direct integration with [`interview-anubi-digital-backend`](https://github.com/fabogit/interview-anubi-digital-backend) running on `http://localhost:3081`.
  * **Utility-First Styling:** Component styling orchestrated through Tailwind CSS 3.0 alongside CSS Modules.

---

## 🛠 Tech Stack

* **Framework & Runtime:** Next.js 12.0.4, React 17.0.2, `react-dom` 17.0.2, Node.js (>= 16)
* **Language & Compiler:** TypeScript 4.5.2, Babel / Next SWC
* **HTTP Client:** Axios 0.27.2
* **Styling & Design:** Tailwind CSS 3.0.24, PostCSS 8.4.13, Autoprefixer 10.4.7
* **Linting & Code Quality:** ESLint 7, `eslint-config-next` 12.0.4

---

## ✨ Features & Endpoints

* **SSR Transaction Ledger:** Real-time retrieval and server rendering of active cryptocurrency transaction logs.
* **Responsive Data Table:** Multi-column display covering date formatting, user identification, transaction values, nature tags, and asset identifiers.
* **Brand Customization:** Styled header, company logos, and themed badges.

### Client Pages & Routes

| Route | Type | Description |
|---|---|---|
| `/` | SSR Page | Primary dashboard rendering transactions fetched from `http://localhost:3081/v1/transactions`. |
| `/api/hello` | API Route | Default Next.js boilerplate API handler. |

---

## 🚀 Getting Started

### Prerequisites

* Node.js `>= 16.0.0`
* Active running instance of [`interview-anubi-digital-backend`](https://github.com/fabogit/interview-anubi-digital-backend) on port `3081`

### Installation

```bash
# Clone the repository
git clone https://github.com/fabogit/interview-anubi-digital-frontend.git
cd interview-anubi-digital-frontend

# Install dependencies
npm install
```

### Environment Configuration

Configure an environment variable for the backend endpoint by creating a `.env.local` file:

```env
NEXT_PUBLIC_API_URL="http://localhost:3081"
```

### Running the Application

```bash
# Start development server (listens on port 3000)
npm run dev

# Production build and execution
npm run build
npm run start
```

Access the frontend dashboard at [http://localhost:3000](http://localhost:3000).

---

## 📄 License & Author

Developed by [@fabogit](https://github.com/fabogit).
