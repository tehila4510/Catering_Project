<div align="center">

# Catering Project

### An elegant full-stack platform for ordering premium catering online

Browse dishes, build custom event packages, pay securely, and leave reviews — all wrapped in a luxurious gold-and-black design.

<br />

[![Angular](https://img.shields.io/badge/Client-Angular%2021-DD0031?logo=angular&logoColor=white)](https://angular.dev)
[![Node.js](https://img.shields.io/badge/Server-Node.js-339933?logo=node.js&logoColor=white)](https://nodejs.org)
[![MongoDB](https://img.shields.io/badge/Database-MongoDB-47A248?logo=mongodb&logoColor=white)](https://www.mongodb.com)
[![TypeScript](https://img.shields.io/badge/Language-TypeScript-3178C6?logo=typescript&logoColor=white)](https://www.typescriptlang.org)
[![PayPal](https://img.shields.io/badge/Payments-PayPal-00457C?logo=paypal&logoColor=white)](https://developer.paypal.com)
[![JWT](https://img.shields.io/badge/Auth-JWT-000000?logo=jsonwebtokens&logoColor=white)](https://jwt.io)

</div>

---

## Overview

**Catering Project** is a final project built as a modern, full-stack web application for a premium catering service. Customers can explore the menu, choose an event package, customize the dishes within the package limits, place an order, and pay online through PayPal. Administrators get a dedicated dashboard to manage dishes, packages, orders, and customers.

The system is split into **two independent repositories** — a frontend client and a backend server — that communicate over a REST API.

## Repositories

This project is composed of two dedicated repositories, plus this general overview repository that ties them together.

| Repository | Description | Tech | Link |
|-----------|-------------|------|------|
| **Client** | The Angular single-page application — the entire user interface, customer flows, and admin dashboard. | Angular 21, TypeScript, SCSS, RxJS | [tehila4510/catering-client](https://github.com/tehila4510/catering-client) |
| **Server** | The REST API — authentication, business logic, database access, and payment processing. | Node.js, Express, MongoDB, JWT | [TEHILA5/catering-server](https://github.com/TEHILA5/catering-server) |

> The **client** and the **server** live in separate repositories and are developed independently. This repository is the general hub that documents the project as a whole and points to both.

## Architecture

```
┌────────────────────────────┐         HTTPS / REST          ┌────────────────────────────┐
│         CLIENT (SPA)        │  ─────────────────────────▶   │         SERVER (API)        │
│                             │                               │                             │
│  Angular 21 (standalone)    │      JSON + JWT Bearer         │  Node.js + Express          │
│  Signals · RxJS · SCSS      │  ◀─────────────────────────   │  REST controllers           │
│  PayPal JS SDK              │                               │  JWT auth middleware        │
└────────────────────────────┘                               └──────────────┬──────────────┘
                                                                             │
                                                                             │  Mongoose
                                                                             ▼
                                                                  ┌─────────────────────┐
                                                                  │       MongoDB       │
                                                                  │  Users · Dishes ·   │
                                                                  │  Packages · Orders  │
                                                                  │  · Reviews          │
                                                                  └─────────────────────┘
```

- **Client** (`tehila4510/catering-client`) runs on `http://localhost:4200` and calls the API at `http://localhost:3000/api`.
- **Server** (`TEHILA5/catering-server`) exposes the REST API on `http://localhost:3000` and persists data in MongoDB.
- Authentication uses **JWT** — the client stores the token and attaches it automatically to every protected request.

## Features

### For Customers
- **Browse the menu** — explore dishes grouped by category (starters, main courses, salads, desserts, breads, drinks).
- **Event packages** — pick a package with a per-person price, minimum guest count, and per-category dish limits.
- **Custom orders** — choose your dishes within the package limits, set the event date, number of guests, and delivery address.
- **Secure online payment** — pay via **PayPal** (sandbox integration) with automatic order confirmation.
- **Reviews & ratings** — leave a star rating and comment for packages you have ordered.
- **User accounts** — register, log in, and manage your profile and order history.

### For Administrators
- **Admin dashboard** — a protected area guarded by role-based access.
- **Manage dishes** — create, edit, and remove menu items.
- **Manage packages** — configure prices, minimum guests, and dish limits per category.
- **Manage orders** — review incoming orders and confirm payments.
- **Manage customers** — view the customer base.

### Extras
- **AI agent chat widget** — an in-app assistant to help customers navigate the site.
- **Luxury design system** — a consistent gold / black / white theme with Playfair Display + Inter typography.

## Tech Stack

| Layer | Technologies |
|-------|--------------|
| **Frontend** | Angular 21 (standalone components + signals), TypeScript (strict), SCSS, RxJS, PayPal JS SDK |
| **Backend** | Node.js, Express, MongoDB (Mongoose), JWT authentication, PayPal Server SDK |
| **Tooling** | Angular CLI, ESLint, Prettier, Vitest |

## Getting Started

To run the full application locally you need to start **both** the server and the client.

### Prerequisites
- [Node.js](https://nodejs.org) (LTS recommended)
- [MongoDB](https://www.mongodb.com) running locally or a MongoDB Atlas connection string
- A [PayPal Developer](https://developer.paypal.com) sandbox account (for payments)

### 1. Start the server

```bash
git clone https://github.com/TEHILA5/catering-server.git
cd catering-server
npm install
# create a .env file with your MongoDB URI, JWT secret, and PayPal credentials
npm run dev
```

The API will be available at `http://localhost:3000/api`.

### 2. Start the client

```bash
git clone https://github.com/tehila4510/catering-client.git
cd catering-client
npm install
ng serve
```

The app will be available at `http://localhost:4200`.

> Make sure the server is running before the client so that API requests succeed.

## Project Roadmap / Status

This is a final project demonstrating a complete, production-style full-stack workflow: authentication, role-based authorization, CRUD management, online payments, and reviews.

## Author

Built with care by **Tehila**.

- Client repository: [github.com/tehila4510/catering-client](https://github.com/tehila4510/catering-client)
- Server repository: [github.com/TEHILA5/catering-server](https://github.com/TEHILA5/catering-server)
