# 12-Week Plan — Backend + DevOps Foundations

Each week has one **Build** (the deliverable), a **Learn** list (what you must understand to build it),
a **DSA set** (3 problems, JavaScript), and a **Done when** line. Reference material is deliberately short:
one primary source per week. Use an AI assistant for everything else, but you must be able to explain every line you ship.

Primary sources reused across weeks:
- Node docs (nodejs.org/docs), Express docs, PostgreSQL tutorial (postgresqltutorial.com), Docker docs, GitHub Actions docs.
- DSA: the GeeksforGeeks DSA Udemy course you already have, and NeetCode's problem list for the actual problems.

---

## Week 1 (14–20 Sep) — Linux shell and Git, properly
**Build:** A bash script `backup.sh` that archives a folder with a timestamp, plus your learner repo set up from the template with a README and your first PR merged.
**Learn:** Ubuntu (VM, WSL2, or a cheap VPS). `pwd ls cd mkdir cp mv rm cat less grep find | > >> chmod chown ps kill`. SSH keys. Git: branch, commit, push, PR, review, merge, `git log`, `git diff`, `.gitignore`. Why secrets never go in a repo.
**DSA set:** Two Sum · Best Time to Buy and Sell Stock · Contains Duplicate.
**Done when:** `bash backup.sh ~/projects` produces a dated `.tar.gz`; your repo has 7 daily logs and one merged PR.

## Week 2 (21–27 Sep) — Node without a framework
**Build:** A plain Node HTTP server (`http` module) that serves `GET /tasks` and `POST /tasks` from a JSON file. No Express yet.
**Learn:** Modules (ESM vs CJS), `fs`, `path`, the event loop, callbacks vs promises vs async/await, `process.env`, npm scripts, `package.json`, `nodemon`.
**DSA set:** Valid Anagram · Valid Palindrome · Reverse Words in a String.
**Done when:** `curl` can create and list tasks and the data survives a restart.

## Week 3 (28 Sep–4 Oct) — Express and REST
**Build:** Tasks API v1 in Express: full CRUD in memory, input validation, correct status codes, central error handler, request logging middleware.
**Learn:** Routing, middleware order, `express.json()`, REST conventions, HTTP status codes, validation (zod or express-validator), Postman or `curl`.
**DSA set:** Group Anagrams · Top K Frequent Elements · Two Sum (hash map version, explain the difference).
**Done when:** A Postman collection in the repo exercises every route and every error path.

## Week 4 (5–11 Oct) — PostgreSQL
**Build:** Tasks API v2: `users` and `tasks` tables with a foreign key, a migration script, and the API reading/writing Postgres through `pg`.
**Learn:** Tables, types, primary/foreign keys, one-to-many, `JOIN`, indexes, `EXPLAIN`, migrations (node-pg-migrate or plain SQL files), connection pooling.
**DSA set:** Valid Parentheses · Min Stack · Implement Queue using Stacks.
**Done when:** Fresh database + `npm run migrate` + `npm start` = working API. No manual table creation.

## Week 5 (12–18 Oct) — Auth and security
**Build:** Signup and login; JWT-protected routes; each user sees only their own tasks; rate limiting; helmet; `.env.example` committed, `.env` ignored.
**Learn:** Password hashing (bcrypt), JWT structure and expiry, `Authorization: Bearer`, OWASP top 3 for APIs (injection, broken auth, broken access control), CORS basics.
**DSA set:** Reverse Linked List · Merge Two Sorted Lists · Linked List Cycle.
**Done when:** User A cannot read, edit or delete User B's tasks, and you can demonstrate it.

## Week 6 (19–25 Oct) — Tests and code quality
**Build:** Jest + Supertest suite covering auth and CRUD (happy paths and the main failures). ESLint + Prettier configured. `npm test` and `npm run lint` pass. README explains setup in under 2 minutes.
**Learn:** Unit vs integration tests, test databases, fixtures, coverage, what a good README contains.
**DSA set:** Binary Search · Find First and Last Position · Search in Rotated Sorted Array.
**Done when:** A stranger can clone, follow the README, and run green tests.

**Call: Sunday 25 Oct, 8pm — mid-cycle demo.**

## Week 7 (26 Oct–1 Nov) — Docker
**Build:** `Dockerfile` (multi-stage, non-root user) and `docker-compose.yml` running API + Postgres with a volume, env vars, and a health check.
**Learn:** Images vs containers, layers and caching, `.dockerignore`, volumes, networks, `docker compose logs`, healthchecks.
**DSA set:** Maximum Subarray · Longest Substring Without Repeating Characters · Container With Most Water.
**Done when:** `docker compose up` on a clean machine gives a working API, and `docker compose down -v` then `up` reproduces it.

## Week 8 (2–8 Nov) — CI with GitHub Actions
**Build:** A workflow that runs lint + tests on every PR, builds the image on `main`, and pushes it to GitHub Container Registry. Branch protection requires green checks.
**Learn:** Workflow YAML, triggers, jobs and steps, services (Postgres in CI), secrets, caching `node_modules`, `GITHUB_TOKEN` permissions.
**DSA set:** Fibonacci with memoization · Subsets · Permutations.
**Done when:** A PR with a failing test cannot be merged; a merge to `main` produces a tagged image in GHCR.

## Week 9 (9–15 Nov) — Deploy to a real server
**Build:** The API live on HTTPS at a real domain or subdomain: Ubuntu VPS, `ufw`, Docker installed, nginx reverse proxy, TLS via certbot, Postgres in a container with a persistent volume.
**Learn:** Provisioning a VPS, SSH hardening (keys only, no root login), nginx basics, DNS A records, Let's Encrypt, backups of the DB volume.
**DSA set:** Maximum Depth of Binary Tree · Invert Binary Tree · Binary Tree Level Order Traversal.
**Done when:** `https://api.<yourname>.<domain>/health` returns 200 from a phone on mobile data.

## Week 10 (16–22 Nov) — Continuous deployment and observability
**Build:** Merge to `main` deploys automatically (Actions → SSH → pull image → restart). Structured JSON logs with pino. `/health` checks the DB. An uptime monitor pings it. A documented rollback to the previous image tag.
**Learn:** Deploy pipelines, zero-downtime restarts (basic), log levels, correlation IDs, what to alert on, RTO/RPO in plain words.
**DSA set:** Validate BST · Lowest Common Ancestor of a BST · Kth Smallest Element in a BST.
**Done when:** You break production on purpose in the call, show the alert, and roll back in under 5 minutes.

## Week 11 (23–29 Nov) — A client on top
**Build:** A small React app (Vite) with login, task list, create/complete/delete, talking to your API with JWT. Deployed on Vercel or Netlify. CORS configured properly.
**Learn:** Fetch with auth headers, token storage trade-offs, loading and error states, environment variables in a frontend build.
**DSA set:** Number of Islands · Flood Fill · Clone Graph.
**Done when:** Your mum can use it from her phone.

## Week 12 (30 Nov–6 Dec) — Ship and present
**Build:** Final README with an architecture diagram, a runbook (how to deploy, roll back, restore the DB), a 5-minute demo video, and a one-page "what I learned" note.
**Mock interview:** 30 min with Shina: walk through the system, then 2 DSA problems from the cycle live.
**DSA set:** Re-solve any 3 problems from earlier weeks without looking.
**Done when:** You would be comfortable sending the repo link to a hiring manager today.

**Call: Sunday 6 Dec, 8pm — final demos and next-cycle decision.**

---

## Later (parking lot, not this cycle)
Kubernetes · Terraform · System design theory · Flutter/React Native · Web3 · Redis and caching · Message queues · GraphQL.
