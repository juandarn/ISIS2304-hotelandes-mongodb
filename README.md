# 🏨 Hotel de los Andes – ISIS2304 (Project · MongoDB · Spring Boot)

Academic project for the course **ISIS2304 – Transactional Systems**.  
The goal is to design a **document-oriented model**, validate schemas, and **implement CRUD operations + analytical queries** for the *Hotel de los Andes* case study using **MongoDB** with **Spring Boot** (REST API and optional web views).

---

## 🎯 Objectives (according to the brief)
- Develop a **conceptual model** (UML / E-R) for the hotel domain.  
- Create a **document model in MongoDB** with **schema validation**.  
- Implement **7 CRUD functionalities (RF1–RF7)** and **queries (RFC1–RFC3 + one advanced query)**.  
- Include **test scenarios** (UI or Postman) and validation-breaking scripts.  
- Deliver all technical documentation and scripts.

---

## 🧩 Functional Scope

**CRUD Features (RF):**
- **RF1:** Room types  
- **RF2:** Rooms  
- **RF3:** Hotel services (pool, spa, bar, restaurant, etc.)  
- **RF4:** Room reservations  
- **RF5:** Check-in process  
- **RF6:** Service consumptions (linked to a room/client)  
- **RF7:** Check-out process  

**Queries (RFC):**
- **RFC1:** Revenue collected by services per room (past year).  
- **RFC2:** Occupancy rate per room (past year).  
- **RFC3:** Customer consumption over a specific date range.  
- **Advanced Query (choose one):** RFC4 / RFC5 / RFC6 / RFC7.

> ⚠️ **Excluded:** user management (roles), consumption plans, or service pre-booking (only on-demand usage).

---

## 🏗️ Data Design and Modeling

- **Conceptual model:** `docs/modelo-conceptual.pdf` (UML/E-R).  
- **Association strategies:**  
  - **Embedded documents** for tightly coupled 1:N relationships (e.g., items inside a consumption).  
  - **Referenced documents** for N:M or independently growing entities (e.g., client ↔ reservations).  
- **Schemas and validation:** `db/schemas/` (JSON Schema per collection).  
  - Validation implemented via `validator` and `jsonSchema` (MongoDB Compass or mongosh).

**Suggested Collections:**
- `roomTypes`, `rooms`, `services`, `reservations`, `checkins`, `checkouts`, `consumptions`, `clients`.

---

## 🧪 Testing and Quality Assurance

- **Backend tests:** JUnit + Spring Boot Test + Mockito.  
- **Postman collections:** endpoint validation (successful and failure cases).  
- **Schema validation:** scripts that attempt to **insert invalid documents** (should fail).  
- **Seed data:** `db/seed/seed.js` used to populate the database for query testing.

---

## ⚙️ Technologies

| Category | Tools |
|-----------|-------|
| Backend | **Java 17, Spring Boot, Maven** |
| Database | **MongoDB 7** (Atlas or local), Spring Data MongoDB |
| DB Tools | MongoDB Compass, mongosh |
| Quality | JUnit, Mockito, (optional) SonarQube |
| Project Management | Git + GitHub (Projects, Wiki) |
| Documentation | Markdown (`docs/` folder) |

---

## 🧾 `application.properties` (example)

```properties
# --- MongoDB (Atlas or local)
spring.data.mongodb.uri=${MONGODB_URI}
spring.data.mongodb.database=hotelandes

# --- Server
server.port=8080

# --- Logging
logging.level.org.springframework.data.mongodb.core.MongoTemplate=INFO
logging.level.edu.uniandes.hotelandes=INFO
````

Create a `.env` file (or set as environment variable):

```
MONGODB_URI=mongodb+srv://<user>:<pass>@<cluster>/<db>?retryWrites=true&w=majority
```

*(Or use `mongodb://localhost:27017/hotelandes` for local development.)*

---

## 🚀 How to Run

### 1) Create collections and validation

```bash
mongosh "$MONGODB_URI" --file db/schemas/create_collections.js
```

### 2) Load seed data (optional)

```bash
mongosh "$MONGODB_URI" --file db/seed/seed.js
```

### 3) Run the Spring Boot application

```bash
mvn clean spring-boot:run
```

* API base: `http://localhost:8080/api/...`
* Web views (if applicable): `http://localhost:8080/`

---

## 📊 Workload Overview

Include in `docs/workload/`:

* **Entities and attributes**, expected data volumes.
* **Read/write frequencies** per entity (Annex A/B).
* **Embedded vs referenced decisions** (Annex C).
* **JSON examples** of data and schema associations (Annex D).

---

## 👥 Team

| Name                | GitHub                                           |
| ------------------- | ------------------------------------------------ |
| **Juan David Rios** | [@juandarn](https://github.com/juandarn)         |
| **Laura Carretero** | [@lauths12](https://github.com/lauths12)         |
| **Gabriel Guevara** | [@BetelgeuseRL](https://github.com/BetelgeuseRL) |

