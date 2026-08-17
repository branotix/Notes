# Golang Backend Engineering — নোটস রিপো

এই রিপোজিটরিতে Golang ব্যাকএন্ড ইঞ্জিনিয়ারিং শেখার সময়কার সব মডিউলের নোট, কমান্ড এবং রিভিশন পয়েন্ট রাখা হবে। ভবিষ্যতে ভুলে গেলে দ্রুত রিভিশন করার জন্য এবং জব লাইফে রেফারেন্স হিসেবে ব্যবহার করার জন্য এই রিপো বানানো হয়েছে।

---

## মডিউল ০১: Tools ও Docker

### ১. dbdiagram.io

[dbdiagram.io](https://dbdiagram.io/) হলো একটি ফ্রি অনলাইন টুল, যা কোড লিখে দ্রুত ডাটাবেস রিলেশনশিপ ডায়াগ্রাম বা **ERD (Entity-Relationship Diagram)** তৈরি করার জন্য ব্যবহার করা হয়। এটি ব্যবহার করে সহজে টেবিল, কলাম এবং তাদের মধ্যকার সম্পর্কগুলো ফুটিয়ে তোলা যায় — কোনো ড্র্যাগ-ড্রপ ছাড়াই, শুধু কোড লিখে।

### ২. make

`make` হলো একটি **বিল্ড অটোমেশন টুল (Build Automation Tool)**, যা মূলত বড় প্রোগ্রাম বা প্রজেক্ট কম্পাইল এবং বিল্ড করার প্রক্রিয়াকে স্বয়ংক্রিয় (Automate) করে।

সহজ ভাষায়, একটি প্রজেক্ট রান বা বিল্ড করতে যদি বারবার অনেকগুলো বড় বড় টার্মিনাল কমান্ড টাইপ করতে হয়, তবে `make` ব্যবহার করে সেই সব কমান্ডকে একটি মাত্র ছোট কমান্ডে (`make build` বা `make run`) রূপান্তর করে ফেলা যায়। এটি সাধারণত Linux এবং macOS-এ বিল্ট-ইন থাকে।

### ৩. sqlc

[sqlc](https://sqlc.dev/) হলো একটি আধুনিক **কোড জেনারেটর টুল (Code Generation Tool)**, যা লেখা Raw SQL কোডকে বিশ্লেষণ করে স্বয়ংক্রিয়ভাবে টাইপ-সেফ (Type-safe) প্রোগ্রামিং কোডে রূপান্তর করে। এটি মূলত Go (Golang) ডেভেলপারদের মধ্যে অত্যন্ত জনপ্রিয়, তবে বর্তমানে Python, TypeScript এবং Kotlin-ও সাপোর্ট করে।

সহজ কথায়, ডাটাবেসের টেবিল ডিজাইন (Schema) এবং প্রয়োজনীয় SQL কোয়েরিগুলো সাধারণ `.sql` ফাইলে লিখে রাখতে হয়। `sqlc` কমান্ড চালালে এটি নিজে থেকেই সেই কোয়েরিগুলোর জন্য ফাংশন এবং ডাটা স্ট্রাকচার (Struct) তৈরি করে দেয়।

### ৪. Docker কী?

Docker হলো একটি ওপেন-সোর্স সফটওয়্যার বা প্ল্যাটফর্ম, যার মাধ্যমে যেকোনো অ্যাপ্লিকেশনকে তার প্রয়োজনীয় সমস্ত কোড, লাইব্রেরি ও ডিপেনডেন্সি সহ একটি নির্দিষ্ট প্যাকেজে বন্দি করা যায়। এই প্যাকেজটিকে বলা হয় **কনটেইনার (Container)**।

সহজ ভাষায়, ডকার ব্যবহার করলে একটি অ্যাপ্লিকেশন নিজের কম্পিউটারে যেভাবে চলবে, ক্লায়েন্টের কম্পিউটার বা লাইভ সার্ভারেও ঠিক একইভাবে (কোনো এরর ছাড়াই) চলবে। এটি ডেভেলপারদের "আমার কম্পিউটারে কাজ করে, কিন্তু সার্ভারে করে না" — এই চিরচেনা সমস্যা থেকে মুক্তি দেয়।

**Docker শেখা মানে আসলে কী?**

আগে এমন হতো — একজন ডেভেলপার কোড লিখলেন এবং নিজের কম্পিউটারে অ্যাপ চালিয়ে দেখলেন একদম ঠিকঠাক কাজ করছে। কিন্তু সেই কোড যখন সার্ভারে বা অন্য কোনো ডেভেলপারের কম্পিউটারে চালানো হতো, তখন দেখা যেত কোনো লাইব্রেরি বা এনভায়রনমেন্টের অমিলের কারণে অ্যাপটি ক্র্যাশ করছে! বলা হতো — "It works on my machine!"

Docker এই সমস্যার সমাধান করেছে। Docker শেখা মানে:
1. কোড, প্রয়োজনীয় লাইব্রেরি, ডিপেনডেন্সি এবং ডিপ্লয়মেন্ট এনভায়রনমেন্টকে একটি "কন্টেইনার"-এর ভেতর প্যাক করা শেখা।
2. যাতে সেই অ্যাপটি ল্যাপটপ, সার্ভার বা যেকোনো ক্লাউডে (AWS, Azure, Google Cloud) অবিকল একইভাবে চলে।

---

### Docker কমান্ড

#### ক. Container ম্যানেজ করার কমান্ড

| কমান্ড | কাজের বিবরণ |
|---|---|
| `docker run <image_name>` | একটি ইমেজ থেকে নতুন কন্টেইনার তৈরি করে চালায় |
| `docker run -d <image_name>` | কন্টেইনারকে ব্যাকগ্রাউন্ডে (Detached mode) চালায় |
| `docker run -p 8080:80 <image_name>` | হোস্ট পিসির পোর্ট (৮০৮০) কন্টেইনারের পোর্টের (৮০) সাথে কানেক্ট করে |
| `docker run --name <name> <image>` | কন্টেইনারের একটি নির্দিষ্ট নাম দেয় |
| `docker ps` | বর্তমানে চালু থাকা (Active) কন্টেইনারের লিস্ট দেখায় |
| `docker ps -a` | সব কন্টেইনারের লিস্ট দেখায় (চালু বা বন্ধ) |
| `docker stop <container_id/name>` | চালু থাকা কন্টেইনার বন্ধ করে |
| `docker start <container_id/name>` | বন্ধ থাকা কন্টেইনার আবার চালু করে |
| `docker restart <container_id/name>` | কন্টেইনার রিস্টার্ট করে |
| `docker rm <container_id/name>` | বন্ধ থাকা কোনো কন্টেইনার মুছে ফেলে |
| `docker rm -f <container_id/name>` | জোরপূর্বক (Forcefully) চালু থাকা কন্টেইনার বন্ধ করে মুছে ফেলে |

#### খ. Docker Image সংক্রান্ত কমান্ড

| কমান্ড | কাজের বিবরণ |
|---|---|
| `docker images` | পিসিতে ডাউনলোড বা তৈরি করা সব ইমেজের লিস্ট দেখায় |
| `docker pull <image_name>` | Docker Hub থেকে নতুন ইমেজ ডাউনলোড করে আনে (রান না করে) |
| `docker rmi <image_name/id>` | কোনো ইমেজ লোকাল পিসি থেকে মুছে ফেলে |
| `docker build -t <tag_name> .` | কোনো Dockerfile থেকে নতুন নিজস্ব ইমেজ বিল্ড বা তৈরি করে |
| `docker history <image_name>` | একটি ইমেজ কীভাবে তৈরি হয়েছে তার লেয়ারগুলো দেখায় |

#### গ. Debugging ও Logs দেখার কমান্ড

| কমান্ড | কাজের বিবরণ |
|---|---|
| `docker logs <container_id/name>` | কন্টেইনারের ভেতরের প্রিন্ট বা লগগুলো দেখায় |
| `docker logs -f <container_id/name>` | রিয়েল-টাইমে কন্টেইনারের লাইভ লগ দেখতে থাকে |
| `docker exec -it <container_id> bash` | চালু থাকা কন্টেইনারের ভেতরে ঢুকে (Terminal) কাজ করার জন্য ব্যবহার হয় |
| `docker top <container_id>` | কন্টেইনারের ভেতরে কোন প্রসেসগুলো চলছে তা দেখায় |
| `docker inspect <container_id/image>` | কন্টেইনার বা ইমেজের বিস্তারিত তথ্য (IP address, Network, Port) JSON ফরম্যাটে দেখায় |

#### ঘ. System Clean-up (জায়গা খালি করার কমান্ড)

| কমান্ড | কাজের বিবরণ |
|---|---|
| `docker system prune` | অপ্রয়োজনীয় বন্ধ থাকা কন্টেইনার, নেটওয়ার্ক ইত্যাদি সব একসাথে মুছে জায়গা খালি করে |
| `docker system prune -a` | ব্যবহার হচ্ছে না এমন সব কন্টেইনার এবং সব ইমেজ ডিলিট করে দেয় |
| `docker system df` | Docker কতটুকু হার্ডডিস্ক স্পেস ব্যবহার করছে তা দেখায় |

#### ঙ. Docker Compose (মাল্টি-কন্টেইনার চালানো)

যখন একটি অ্যাপে একসাথে একাধিক জিনিস লাগে (যেমন: Node.js App + Database MongoDB + Redis Cache), তখন Docker Compose দিয়ে এক কমান্ডেই সব চালানো যায়:

| কমান্ড | কাজের বিবরণ |
|---|---|
| `docker compose up` | `docker-compose.yml` ফাইলের সব সার্ভিস তৈরি করে চালু করে |
| `docker compose up -d` | ব্যাকগ্রাউন্ডে সার্ভিসগুলো চালু করে |
| `docker compose down` | Compose দিয়ে চালু করা সব কন্টেইনার এক ক্লিকে বন্ধ ও মুছে ফেলে |
| `docker compose logs -f` | সব সার্ভিসের লগ একসাথে দেখায় |

---

### Code Examples: PostgreSQL Docker-এ চালানো

**১. PostgreSQL কন্টেইনার চালু করা**

```bash
docker run --name my-postgres \
  -e POSTGRES_USER=admin \
  -e POSTGRES_PASSWORD=mysecretpassword \
  -e POSTGRES_DB=mydb \
  -p 5432:5432 \
  -v postgres_data:/var/lib/postgresql/data \
  -d postgres
```

**ফ্ল্যাগের ব্যাখ্যা:**
- `--name my-postgres` — কন্টেইনারের একটি নাম দেওয়া (যাতে সহজে অ্যাক্সেস করা যায়)
- `-e POSTGRES_...` — ইউজার, পাসওয়ার্ড ও ডাটাবেজ সেট করা
- `-p 5432:5432` — পিসির `5432` পোর্টের সাথে কন্টেইনারের `5432` পোর্ট কানেক্ট করা
- `-v postgres_data:/var/lib/postgresql/data` — ভলিউম (Volume) মাউন্ট করা। সবচেয়ে গুরুত্বপূর্ণ, কারণ কন্টেইনার বন্ধ বা ডিলিট হয়ে গেলেও ডাটা নষ্ট হবে না (Data Persistence)
- `-d` — কন্টেইনারটি ব্যাকগ্রাউন্ডে চালু রাখার জন্য (Detached mode)
- `postgres` — অফিশিয়াল ইমেজের নাম (নির্দিষ্ট ভার্সন চাইলে `postgres:16` বা `postgres:15` লেখা যায়)

**২. কন্টেইনারের ভেতরে ঢুকে psql-এ প্রবেশ করা**

```bash
docker exec -it my-postgres psql -U admin -d mydb
```

(এখানে `-U` দিয়ে ইউজারনেম এবং `-d` দিয়ে ডাটাবেজ নেম নির্দেশ করা হয়েছে।)

**৩. ব্যাকআপ নেওয়া এবং রিস্টোর করা**

ব্যাকআপ (Dump) তৈরি করতে:
```bash
docker exec -t my-postgres pg_dump -U admin mydb > backup.sql
```

ব্যাকআপ ফাইল থেকে ডাটা রিস্টোর করতে:
```bash
cat backup.sql | docker exec -i my-postgres psql -U admin -d mydb
```

**৪. স্বয়ংক্রিয় স্ক্রিপ্ট চালু করা (Initialization Scripts)**

কন্টেইনার প্রথমবার চালু হওয়ার সময়ই নির্দিষ্ট কিছু টেবিল বা ডাটা স্বয়ংক্রিয়ভাবে তৈরি করতে চাইলে, `.sql` বা `.sh` ফাইল কন্টেইনারের `/docker-entrypoint-initdb.d/` ফোল্ডারে মাউন্ট করে দেওয়া যায়:

```bash
-v /your/local/init.sql:/docker-entrypoint-initdb.d/init.sql
```

**৫. Docker Compose দিয়ে সহজ কনফিগারেশন**

বারবার লম্বা কমান্ড না লিখে একটি `docker-compose.yml` ফাইল তৈরি করে সহজে চালানো যায়:

```yaml
version: '3.8'

services:
  db:
    image: postgres:16
    container_name: postgres-db
    restart: always
    environment:
      POSTGRES_USER: admin
      POSTGRES_PASSWORD: mysecretpassword
      POSTGRES_DB: mydb
    ports:
      - "5432:5432"
    volumes:
      - postgres_data:/var/lib/postgresql/data

volumes:
  postgres_data:
```

চালু করার কমান্ড:
```bash
docker compose up -d
```

---

### ৫. golang-migrate ইনস্টল করা (অফিশিয়াল পদ্ধতি)

Docker ও PostgreSQL সেটআপ শেষ করার পরে শেখা — `golang-migrate` হলো ডাটাবেস মাইগ্রেশন টুল। অফিশিয়াল ওয়েবসাইটের মতো Variable সেট করে ইনস্টল করার পদ্ধতি:

```bash
export version=v4.17.0
export os=linux
export arch=amd64

curl -L https://github.com/golang-migrate/migrate/releases/download/$version/migrate.$os-$arch.tar.gz | tar xvz
sudo mv migrate /usr/local/bin/
migrate -version
```

**ব্যাখ্যা:**
- `export version=v4.17.0` — কোন ভার্সন ইনস্টল করা হবে সেটা variable-এ সেট করা
- `export os=linux` — অপারেটিং সিস্টেম (macOS হলে `darwin`)
- `export arch=amd64` — সিস্টেম আর্কিটেকচার
- `curl -L ... | tar xvz` — GitHub রিলিজ থেকে বাইনারি ডাউনলোড করে সরাসরি এক্সট্র্যাক্ট করা
- `sudo mv migrate /usr/local/bin/` — এক্সট্র্যাক্ট করা বাইনারিটা সিস্টেম PATH-এ move করা, যাতে যেকোনো জায়গা থেকে `migrate` কমান্ড চালানো যায়
- `migrate -version` — ইনস্টল ঠিকমতো হয়েছে কিনা যাচাই করা

---
# Migration, Docker & Makefile Setup Guide

এই প্রজেক্টে আমরা **Docker**, **Makefile**, এবং **Golang Migrate** ব্যবহার করে একটি ডাটাবেস মাইগ্রেশন প্রসেস ও প্রজেক্ট সেটআপ শিখব।

---

## 📂 Project Folder Structure

প্রজেক্টের প্রাথমিক ফোল্ডার ও ফাইল স্ট্রাকচার:

```text
.
├── Makefile
└── db/
    └── migration/

---

### Quick Revision Points

- **dbdiagram.io** — কোড লিখে দ্রুত ERD (ডাটাবেস ডায়াগ্রাম) বানানোর ফ্রি টুল।
- **make** — লম্বা টার্মিনাল কমান্ডকে ছোট কমান্ডে (`make build`) রূপান্তর করে দেয় বিল্ড অটোমেশনের জন্য।
- **sqlc** — Raw SQL থেকে টাইপ-সেফ Go কোড (ফাংশন/struct) অটো-জেনারেট করে।
- **Docker** = কোড + লাইব্রেরি + ডিপেনডেন্সি → এক কন্টেইনারে প্যাক → সব জায়গায় একই আচরণ (no "works on my machine" সমস্যা)।
- কন্টেইনার চালাতে `docker run`, লিস্ট দেখতে `docker ps`, ভেতরে ঢুকতে `docker exec -it <id> bash`।
- ডাটা যেন হারিয়ে না যায় সেজন্য সবসময় `-v` দিয়ে volume মাউন্ট করা জরুরি।
- একাধিক সার্ভিস একসাথে চালাতে হলে `docker-compose.yml` + `docker compose up -d`।
- ব্যাকআপ নিতে `pg_dump`, রিস্টোর করতে `psql`-এ pipe করে।
- **golang-migrate** — `export` দিয়ে version/os/arch সেট করে GitHub রিলিজ থেকে বাইনারি ডাউনলোড ও `/usr/local/bin/`-এ move করে ইনস্টল করা হয়; `migrate -version` দিয়ে যাচাই করা যায়।

---

> নতুন মডিউল শেষ হলে এই ফাইলে নিচে নতুন সেকশন (মডিউল ০২) যোগ হবে।
