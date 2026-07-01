# MarketingHub — Project Notes
**Developer:** Akhil  
**Stack:** Java + Spring Boot | React + Tailwind | PostgreSQL | WebSockets | Docker  
**Repo:** https://github.com/Akhil588335/marketinghub  
**Project Path:** C:\akhil project\marketinghub  

---

## HOW TO USE THESE NOTES
- These notes live inside your repo — every time you push code, notes push with it.
- One entry per day. Format: **What I did → Why it matters → What I learned.**
- At key milestones (end of each week), a PDF export is generated.
- Don't write essays — bullet points that *you* can re-read in 60 seconds and understand.

---

## WEEK 0 — Environment Setup

### Day 1 — Tool Installation + GitHub Repo

**What I did:**
- Installed JDK 25 (Eclipse Temurin) — verified with `java -version`
- Installed IntelliJ IDEA 2026 (Community/Trial)
- Installed Git 2.55 — verified with `git --version`
- Installed Node.js v24 + npm 11 — verified with `node -v` and `npm -v`
- Installed Postman
- Created empty GitHub repo: https://github.com/Akhil588335/marketinghub

**Why it matters:**
- JDK is the Java runtime — without it, no Java code runs at all.
- IntelliJ is the IDE (code editor) purpose-built for Java/Spring Boot. It handles project structure, auto-imports, and running your app.
- Git tracks every change you make to your code. GitHub stores it remotely — so your work is never lost and visible to recruiters.
- Node.js is needed for React (frontend), even though the backend is Java. You install it now so it's ready when you reach Week 3.
- Created repo EMPTY (no README checked) to avoid merge conflicts when we push the Spring Boot project into it later.

**What I learned:**
- Tools don't just "install and forget" — each serves a specific role in the development pipeline. JDK = runtime, IntelliJ = editor, Git = version control, Node = frontend tooling.
- Port 5432 is PostgreSQL's default port. Port 8080 is Spring Boot's default HTTP port. Knowing defaults saves debugging time.

---

### Day 2 — Spring Boot Project Generation + PostgreSQL Setup + First Successful Run

**What I did:**
- Generated Spring Boot project via IntelliJ Spring Initializr with these settings:
  - Group: `com.akhil` | Artifact: `marketinghub`
  - Language: Java | Type: Maven | Packaging: Jar | Java: 21
  - Dependencies: Spring Web, Spring Data JPA, PostgreSQL Driver, Lombok, Spring Boot DevTools
- Installed PostgreSQL 18 locally (port 5432, username: `postgres`)
- Created database `marketinghub_db` in pgAdmin 4
- Configured `application.properties` to connect Spring Boot to the database
- Successfully ran the app — "Started MarketinghubApplication in 5.489 seconds"

**The project structure generated:**
```
marketinghub/
├── src/main/java/com/akhil/marketinghub/
│   └── MarketinghubApplication.java      ← Entry point (@SpringBootApplication)
├── src/main/resources/
│   └── application.properties            ← Config (DB URL, credentials, JPA settings)
├── src/test/java/com/akhil/marketinghub/
│   └── MarketinghubApplicationTests.java ← Auto-generated test
└── pom.xml                               ← Maven dependency list
```

**application.properties explained line by line:**
```properties
spring.application.name=marketinghub
# Sets the app name — appears in logs and monitoring tools

spring.datasource.url=jdbc:postgresql://localhost:5432/marketinghub_db
# jdbc = Java Database Connectivity (protocol)
# postgresql = database type
# localhost:5432 = where PostgreSQL is running (local machine, default port)
# marketinghub_db = the specific database to use

spring.datasource.username=postgres
# 'postgres' is the default superuser created during PostgreSQL install

spring.datasource.password=Akhil6854#
# The password set during PostgreSQL installation — NEVER share this publicly

spring.jpa.hibernate.ddl-auto=update
# Tells Hibernate to auto-create/update database tables from @Entity classes
# 'update' = safe for development (won't delete data)
# WARNING: Never use 'update' in production — use Flyway/Liquibase instead

spring.jpa.show-sql=true
# Prints the actual SQL Hibernate generates to the console — great for learning

spring.jpa.properties.hibernate.dialect=org.hibernate.dialect.PostgreSQLDialect
# Tells Hibernate to generate PostgreSQL-specific SQL syntax
# (Note: newer Hibernate auto-detects this, but explicit is fine)
```

**Why it matters:**
- Spring Boot needs to know WHERE the database is, WHO to log in as, and HOW to interact with it — that's exactly what application.properties provides.
- The **DataSource** is Spring's abstraction for a database connection. You don't connect directly — Spring manages a pool of reusable connections (via HikariCP) for performance.
- **HikariCP** is the connection pool you saw in logs: `HikariPool-1 - Added connection`. Instead of creating a fresh connection for every request (expensive), it reuses a pool of pre-made ones.
- **`ddl-auto=update`** means once we write @Entity Java classes in Week 2, Hibernate will automatically create the matching PostgreSQL tables. No manual SQL CREATE TABLE needed during development.

**What I learned:**
- Adding a JPA/database dependency makes Spring Boot *require* a DataSource config at startup. Missing config = immediate startup failure. This is "convention over configuration" working both ways — add a capability, configure it correctly.
- Reading Spring Boot startup logs is a skill. A successful boot ends with `Started [AppName] in X.XXX seconds`. A failed boot ends with red `APPLICATION FAILED TO START` + a reason. The reason line is always the most important one to read.
- `localhost` means "this machine itself." `5432` is always PostgreSQL's port unless you manually change it during install.
- The error `Failed to determine a suitable driver class` means Spring Boot found JPA on the classpath but couldn't find database connection config — missing `application.properties` entries, not broken code.

**Key log lines to understand:**
```
HikariPool-1 - Start completed.           → Database connection pool is ready
Tomcat started on port 8080               → Web server is live, ready to accept HTTP requests
Started MarketinghubApplication in 5.489s → Everything initialized, app is running
```

**Errors hit + how we fixed them:**
| Error | Root Cause | Fix |
|-------|-----------|-----|
| `Failed to determine a suitable driver class` | No database config in application.properties | Added datasource URL, username, password |
| Stack Builder popup after PostgreSQL install | It's optional extra tools, not required | Clicked Cancel — no action needed |

---

## COMING UP

| Week | Focus |
|------|-------|
| Week 0 Day 3 | Connect Git to GitHub, push project |
| Week 0 Day 4 | Read old Flask code, write API spec |
| Week 0 Day 5 | Design database schema (ER diagram) |
| Week 0 Day 6 | Git workflow practice |
| Week 1 | Spring Boot fundamentals — first REST controller |

---

*Notes maintained by Akhil + Claude. Updated daily.*

---

### Day 3 — Git Setup + Push to GitHub

**What I did:**
- Initialized Git inside the project: `git init`
- Staged all files: `git add .`
- Made first commit: `git commit -m "Week 0: Initial Spring Boot project setup with PostgreSQL connection"`
- Connected to GitHub remote: `git remote add origin https://github.com/Akhil588335/marketinghub.git`
- Pushed to GitHub: `git push -u origin main`
- Secured credentials using Windows Credential Manager: `git config --global credential.helper manager`
- Fixed commit author name from RohithSiripuram → Akhil588335 using `git commit --amend --reset-author`

**The 3 daily Git commands (use every single day from now):**
```
git add .
git commit -m "describe what you did"
git push
```

**Why it matters:**
- Git is not optional in real development — every company uses it. Your commit history is a public record of your work ethic and consistency, visible to recruiters on GitHub.
- `git add .` = stage all changes (pack the box)
- `git commit` = take a permanent snapshot with a message (seal the box with a label)
- `git push` = upload that snapshot to GitHub (send the box)
- The `-u origin main` flag on first push sets the default remote so future pushes just need `git push`
- `credential.helper manager` = Windows stores your GitHub token securely, so you don't retype it every push

**What I learned:**
- GitHub no longer accepts account passwords for Git operations — requires a Personal Access Token (PAT) instead. PATs are generated under Settings → Developer Settings → Personal Access Tokens.
- Never embed your token directly in the remote URL permanently — use credential manager to store it securely.
- `git commit --amend --reset-author` rewrites the author of the most recent commit without changing its content. Use `--force` push after amending an already-pushed commit.
- Git author identity (`user.name`, `user.email`) is set globally with `git config --global` — it applies to all repos on this machine.

**Errors hit + fixes:**
| Error | Root Cause | Fix |
|-------|-----------|-----|
| `fatal: Authentication failed` | GitHub no longer accepts passwords, needs PAT | Generated Personal Access Token, used it as password |
| Commit showed as RohithSiripuram | Global git user.name was set to a different name | `git config --global user.name "Akhil588335"` + `git commit --amend --reset-author` |

---

### Day 4 — Product Specification (Reading Flask Code + Designing the Real Product)

**What I did:**
- Re-read original Flask demo (app.py) carefully
- Identified what the prototype did vs what the real product should do
- Designed the complete product specification with 3 roles, full flow, and all features

**The real MarketingHub — what it actually is:**
A marketplace where vendors book riders with **digital display screens on their vehicles** to run ad campaigns in specific geographic areas.

**The 3 roles:**

| Role | What they do |
|------|-------------|
| Vendor | Posts ad campaign, picks area + duration + number of riders, pays for it |
| Admin | Reviews and approves/rejects campaigns, verifies rider photos manually |
| Rider | Gets notified of nearby campaigns, accepts/rejects, runs the campaign, earns money |

**Complete campaign flow:**
```
Vendor posts campaign
        ↓
Admin reviews + approves (checks ad content + payment)
        ↓
Nearby riders get notified automatically
        ↓
Riders accept until slots are filled → campaign closes
        ↓
Rider uploads START photo → Admin verifies
        ↓
Rider starts session → GPS tracking begins
        ↓
Every 30 seconds → location logged, distance updated
        ↓
Random interval photos uploaded → Admin verifies
        ↓
Rider ends session → distance + time finalised
        ↓
Rider uploads END photo → Admin verifies
        ↓
Payment = (km × ratePerKm) + (minutes × ratePerMinute)
        ↓
Campaign marked COMPLETED
```

**Data we need to store:**

| Entity | Key Fields |
|--------|-----------|
| User | id, name, email, password, role (VENDOR/RIDER/ADMIN) |
| Rider Profile | id, userId, latitude, longitude, isAvailable, totalEarnings |
| Ad Campaign | id, vendorId, adContent, targetArea, targetLat, targetLng, radiusKm, startTime, duration, ridersNeeded, ridersAccepted, status, amount |
| Campaign Application | id, campaignId, riderId, status, distanceCoveredKm, timeActiveMinutes, earningsCalculated |
| Rider Session | id, applicationId, sessionStartTime, sessionEndTime, isActive |
| Location Log | id, applicationId, latitude, longitude, recordedAt |
| Verification Photo | id, applicationId, photoUrl, capturedAt, type (START/INTERVAL/END), verificationStatus, adminNotes |
| Payment | id, campaignId, riderId, amount, status |

**Full API endpoints designed:**
- Auth: signup, login (JWT)
- Vendor: create campaign, view my campaigns, view riders on map
- Admin: view pending campaigns, approve/reject, view pending photos, verify/fail photos, view pending payments
- Rider: view available campaigns, accept/reject, start/end session, update location, upload verification photo, view earnings
- WebSocket: live location updates, campaign notifications, slot-filled events

**Why it matters:**
- Writing a product spec BEFORE writing code is standard practice in real companies. It prevents "building the wrong thing" — the most expensive mistake in software.
- Thinking through roles, flows, and edge cases now means the database schema (Day 5) and API design will be correct from the start, rather than constantly refactoring.
- The decision to make admin verification manual first, then automate later, is a real engineering principle: validate the process manually before investing in automation.

**What I learned:**
- A prototype (Flask demo) proves an idea works. A specification defines what the real product is. These are two different things.
- Payment logic needs to be in the spec before the database — because how you calculate payment determines what fields you need to store (distance, time, rates).
- "Slots" logic (campaign closes after N riders accept) is a concurrency concern — when we implement it, we'll need database-level locking to prevent 2 riders both accepting the last slot simultaneously.
- Photo verification at START + random INTERVALS + END is a pattern used in real gig economy apps (Swiggy, Dunzo) to prevent fraud.

---

## COMING UP

| Day | Focus |
|-----|-------|
| Week 0, Day 5 | Design ER diagram — all tables, columns, relationships, foreign keys |
| Week 0, Day 6 | Git workflow practice — branching strategy |
| Week 1, Day 1 | First @RestController — GET /api/riders endpoint |
| Week 1, Day 2 | Dependency Injection deep dive |
| Week 1, Days 3-4 | Rebuild all Flask endpoints in Spring Boot |

---

*Notes maintained by Akhil + Claude. Updated daily.*
