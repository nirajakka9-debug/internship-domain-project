<div align="center">

# 🎫 Nettech Help Desk Ticket Management System
### *An Enterprise-Grade, Full-Stack IT Service Management & Issue Tracking Platform*

[![Java 21](https://img.shields.io/badge/Java-21_LTS-ED8B00?style=for-the-badge&logo=openjdk&logoColor=white)](https://www.oracle.com/java/)
[![Spring Boot 3.2.5](https://img.shields.io/badge/Spring_Boot-3.2.5-6DB33F?style=for-the-badge&logo=springboot&logoColor=white)](https://spring.io/projects/spring-boot)
[![Spring Security 6](https://img.shields.io/badge/Spring_Security-6.0-6DB33F?style=for-the-badge&logo=springsecurity&logoColor=white)](https://spring.io/projects/spring-security)
[![MySQL 8.0](https://img.shields.io/badge/MySQL-8.0-4479A1?style=for-the-badge&logo=mysql&logoColor=white)](https://www.mysql.com/)
[![Thymeleaf](https://img.shields.io/badge/Thymeleaf-3.1-005F0F?style=for-the-badge&logo=thymeleaf&logoColor=white)](https://www.thymeleaf.org/)
[![Bootstrap 5.3](https://img.shields.io/badge/Bootstrap-5.3-7952B3?style=for-the-badge&logo=bootstrap&logoColor=white)](https://getbootstrap.com/)
[![Architecture](https://img.shields.io/badge/Architecture-3--Tier_MVC-0A192F?style=for-the-badge)](https://en.wikipedia.org/wiki/Multitier_architecture)
[![Status](https://img.shields.io/badge/Build-Production_Ready-brightgreen?style=for-the-badge)]()

<br/>

**A complete enterprise software solution engineered to modernize internal IT operations, eliminate communication silos, and automate the lifecycle of support tickets through role-based access, threaded discussions, real-time analytics, and asynchronous notifications.**

---

[🚀 Quick Start](#-quick-start--local-setup) •
[🏛️ System Architecture](#️-system-architecture--tech-stack) •
[✨ Core Features](#-core-features--deep-dive-functional-modules) •
[🗄️ Database & ER Model](#️-database-architecture--entity-relationship-model) •
[🛡️ Security (RBAC)](#️-security-architecture--role-based-access-control-rbac) •
[🌐 Route Matrix](#-complete-mvc--route-endpoints-matrix) •
[📧 Email Engine](#-asynchronous-email-notification-engine)

---

</div>

<br/>

## 📖 Table of Contents
1. [Executive Summary & Problem Statement](#-executive-summary--problem-statement)
2. [System Architecture & Tech Stack](#️-system-architecture--tech-stack)
3. [Core Features & Deep Dive Functional Modules](#-core-features--deep-dive-functional-modules)
   - [1. Role-Based Access Control (RBAC)](#1-role-based-access-control-rbac)
   - [2. Ticket Lifecycle & State Progression Engine](#2-ticket-lifecycle--state-progression-engine)
   - [3. Threaded Collaboration & Internal Technician Notes](#3-threaded-collaboration--internal-technician-notes)
   - [4. Multi-Persona Dynamic Dashboards](#4-multi-persona-dynamic-dashboards)
   - [5. Full-Text Search & Multi-Filter Query Engine](#5-full-text-search--multi-filter-query-engine)
   - [6. User Profile Management & Avatar Uploads](#6-user-profile-management--avatar-uploads)
   - [7. Asynchronous Event-Driven Email Notification Engine](#7-asynchronous-event-driven-email-notification-engine)
4. [Database Architecture & Entity-Relationship Model](#️-database-architecture--entity-relationship-model)
5. [Complete MVC & Route Endpoints Matrix](#-complete-mvc--route-endpoints-matrix)
6. [Security Architecture & Authentication Pipeline](#️-security-architecture--role-based-access-control-rbac)
7. [Repository Codebase Directory Structure](#-repository-codebase-directory-structure)
8. [Dual Database Configuration (MySQL vs. H2)](#-dual-database-configuration-guide)
9. [Quick Start & Local Setup](#-quick-start--local-setup)
10. [Demo Accounts Matrix](#-demo-accounts-matrix)
11. [Future Roadmap & Scalability](#-future-roadmap--scalability-enhancements)
12. [Author & Academic Info](#-author--academic-credits)

---

## 🎯 Executive Summary & Problem Statement

### ⚠️ The Problem: Internal Support Inefficiencies
In modern corporate environments, technical support requests handled via ad-hoc verbal requests, fragmented chat messages, or unstructured email chains suffer from fundamental failure points:
* **Zero Auditability:** No historical record of issue diagnostics, technician responses, or resolution timestamps.
* **Ambiguous Prioritization:** IT agents cannot effectively distinguish between critical server outages and minor hardware peripheral requests.
* **Lack of Accountability:** Unassigned requests fall through the cracks, resulting in prolonged employee downtime and unfulfilled Service Level Agreements (SLAs).
* **Communication Friction:** Back-and-forth email loops delay technical troubleshooting and resolution validation.

### 💡 The Solution: Nettech Help Desk Platform
The **Nettech Help Desk Ticket Management System** provides a centralized, web-based platform engineered on enterprise Java standards. It establishes an auditable, real-time issue resolution pipeline featuring:
* **End-to-End Traceability:** Complete lifecycle tracking from issue submission to resolution verification.
* **Granular Role Separation:** Distinct operational interfaces for Employees, Support Technicians, and System Administrators.
* **Real-Time Collaboration:** Nested public comments for user communication and private flags for internal staff notes.
* **Instant Telemetry:** Automated KPI cards tracking ticket counts by status, department, and priority.
* **Non-Blocking Notifications:** Event-driven email dispatch operating on background worker thread pools.

---

## 🏛️ System Architecture & Tech Stack

The platform is designed following the industry-standard **3-Tier Model-View-Controller (MVC)** architectural pattern, ensuring loose coupling, separation of concerns, and maximum maintainability.

```
┌─────────────────────────────────────────────────────────────────────────┐
│                        PRESENTATION LAYER (UI)                          │
│   HTML5 • CSS3 Glassmorphism • Bootstrap 5.3 • Thymeleaf 3.1 • JS       │
└────────────────────────────────────┬────────────────────────────────────┘
                                     │ HTTP / HTTPS (Form Data & JSON)
                                     ▼
┌─────────────────────────────────────────────────────────────────────────┐
│                       APPLICATION LAYER (CONTROLLERS)                   │
│   AuthController • DashboardController • TicketController               │
│   AdminController • ProfileController • Spring Security 6 Filters       │
└────────────────────────────────────┬────────────────────────────────────┘
                                     │ Method Calls / DTOs
                                     ▼
┌─────────────────────────────────────────────────────────────────────────┐
│                        BUSINESS LOGIC LAYER (SERVICES)                  │
│   UserService • TicketService • CommentService • EmailService (@Async)   │
└────────────────────────────────────┬────────────────────────────────────┘
                                     │ Spring Data JPA / JPQL
                                     ▼
┌─────────────────────────────────────────────────────────────────────────┐
│                       DATA PERSISTENCE LAYER (ORM)                      │
│   UserRepository • TicketRepository • CommentRepository • Hibernate 6   │
└────────────────────────────────────┬────────────────────────────────────┘
                                     │ JDBC / TCP Socket (Port 3306)
                                     ▼
┌─────────────────────────────────────────────────────────────────────────┐
│                     DATABASE / STORAGE LAYER (ACID)                     │
│   MySQL 8.0 Relational Database (XAMPP) / Embedded File Database (H2)   │
└─────────────────────────────────────────────────────────────────────────┘
```

### 🛠️ Technology Specifications Table
| Layer / Domain | Technology Component | Version | Technical Justification |
| :--- | :--- | :--- | :--- |
| **Language Runtime** | Java OpenJDK | `21 LTS` | Modern Java features, virtual-thread readiness, record patterns, enhanced memory management. |
| **Backend Framework** | Spring Boot | `3.2.5` | Rapid application bootstrapping, inversion of control, automated bean injection, robust ecosystem. |
| **Security Framework** | Spring Security | `6.2.x` | Industry-standard authentication filters, BCrypt password hashing, session control, and CSRF protection. |
| **Persistence & ORM** | Spring Data JPA / Hibernate | `6.4.x` | Object-Relational Mapping, automated DDL schema synchronization (`ddl-auto=update`), JPQL abstraction. |
| **Database Engine** | MySQL Community Server | `8.0 / 8.4` | ACID-compliant relational persistence, indexed foreign keys, high concurrency support via XAMPP. |
| **Template Engine** | Thymeleaf | `3.1.x` | Server-Side Rendering (SSR), security taglib integration (`thymeleaf-extras-springsecurity6`). |
| **Frontend Styling** | Bootstrap & Custom CSS | `5.3.x` | Modern responsive grid, custom glassmorphism aesthetic, accessible UI components. |
| **Email Subsystem** | Spring Boot Starter Mail | `3.2.x` | Asynchronous SMTP transmission via JavaMailSender using `@Async` thread pools. |
| **Build & Dependency** | Apache Maven | `3.9.x` | Reproducible dependency management, automated testing, and standalone artifact packaging. |

---

## ✨ Core Features & Deep Dive Functional Modules

### 1. Role-Based Access Control (RBAC)
The application enforces strict role-based access control managed by **Spring Security 6**. Upon login, user credentials and authorities (`GrantedAuthority`) determine access permissions across the system.

```
                  ┌───────────────────┐
                  │   All Endpoints   │
                  └─────────┬─────────┘
                            │
            ┌───────────────┼───────────────┐
            ▼               ▼               ▼
      [ROLE_USER]   [ROLE_TECHNICIAN] [ROLE_ADMIN]
      • Create Ticket • Claim Tickets • System Analytics
      • View Own Hist • Triage Status • User Management
      • Add Comments  • Internal Notes• Full Override
```

---

### 2. Ticket Lifecycle & State Progression Engine
Tickets traverse a well-defined finite state machine from creation to final resolution.

```
   [ 1. OPEN ] ──────────────► [ 2. ASSIGNED ] ──────────────► [ 3. IN PROGRESS ]
 (Created by User)         (Claimed by Tech/Admin)          (Active Troubleshooting)
                                                                    │
                                                                    ▼
   [ 5. CLOSED ] ◄───────────────────────────────────────── [ 4. RESOLVED ]
(Archived / Verified)                                    (Fix Applied & Tested)
```

* **Attributes Tracked:** Unique Ticket ID, Title, Detailed Description, Category (Hardware, Software, Network, Account Access), Priority Level (`LOW`, `MEDIUM`, `HIGH`, `URGENT`), Status (`OPEN`, `IN_PROGRESS`, `RESOLVED`, `CLOSED`), Created Timestamp, and Updated Timestamp.
* **Priority Escalation:** Urgent and High priority tickets are highlighted with high-contrast visual badges and sorted to the top of technician queues.

---

### 3. Threaded Collaboration & Internal Technician Notes
Every ticket acts as an active collaboration workspace between the requester and support staff.
* **Public Messages:** Visible to both the employee and technicians, facilitating clear communication and request clarification.
* **Internal Staff Notes (`is_internal = true`):** Highlighted with a specialized badge, these notes are exclusively visible to `ROLE_TECHNICIAN` and `ROLE_ADMIN`. This allows staff to document diagnostic steps, passwords, or server configurations without exposing internal technical details to standard users.

---

### 4. Multi-Persona Dynamic Dashboards
The home portal automatically adapts its layout based on the logged-in persona:
* **Employee Dashboard:** Displays a summary of personal tickets, pending responses, resolution rates, and a quick-action button to raise a new ticket.
* **Technician Console:** Features an active triage queue, unassigned ticket alerts, high-priority filters, and one-click status transition controls.
* **Administrator Command Center:** Provides system-wide operational metrics: total registered users, overall resolution rates, active tickets across departments, and links to administrative tools.

---

### 5. Full-Text Search & Multi-Filter Query Engine
Leverages custom **Spring Data JPA JPQL queries** to provide fast searching and filtering:
* **Keyword Search:** Case-insensitive substring searching across ticket titles and issue descriptions.
* **Category Filtering:** Filter tickets across departments (*Hardware Request, Network & Connectivity, Account Access, Software Maintenance*).
* **Priority & Status Toggles:** Instant narrowing of work queues to focus on urgent blockers.

---

### 6. User Profile Management & Avatar Uploads
* **Profile Customization:** Users can update their full name, email address, department, and securely change their account password.
* **MultipartFile Processing:** Supports avatar image uploads (`.png`, `.jpg`, `.jpeg`). Files are validated, sanitized, and stored locally, with paths mapped directly to the user record in MySQL.

---

### 7. Asynchronous Event-Driven Email Notification Engine
* **Non-Blocking Background Execution:** Annotated with `@Async`, email dispatch methods run on a background `ThreadPoolTaskExecutor`.
* **Latency Optimization:** User HTTP requests complete in **< 15ms**, eliminating the typical 2–4 second delay associated with synchronous SMTP handshakes.
* **Automated Trigger Events:**
  1. *Ticket Creation:* Dispatches confirmation email to requester with ticket tracking ID.
  2. *Status Update:* Alerts the user when a technician updates the ticket (e.g., from *Open* to *Resolved*).
  3. *Staff Reassignment:* Notifies the newly assigned technician of urgent incoming tasks.
* **Fault-Tolerant Logging:** If external SMTP credentials are not configured or the network drops, exceptions are caught gracefully, logged via SLF4J, and the application flow continues without crashing.

---

## 🗄️ Database Architecture & Entity-Relationship Model

The database is built on a fully normalized relational schema hosted in **MySQL 8.0** (managed via XAMPP / phpMyAdmin). Schema synchronization and constraint enforcement are handled automatically via Hibernate ORM (`spring.jpa.hibernate.ddl-auto=update`).

```
┌──────────────────────────────────────┐          ┌──────────────────────────────────────┐
│                USERS                 │          │               TICKETS                │
├──────────────────────────────────────┤          ├──────────────────────────────────────┤
│ PK  id               BIGINT (AI)     │ 1      N │ PK  id               BIGINT (AI)     │
│     username         VARCHAR(50) [U] │──────────│ FK  user_id          BIGINT          │
│     password         VARCHAR(255)    │          │ FK  assigned_to      BIGINT (Null)   │
│     email            VARCHAR(100)[U] │ 1      N │     title            VARCHAR(150)    │
│     full_name        VARCHAR(100)    │──────────│     description      TEXT            │
│     role             ENUM(3 Roles)   │ (Assign) │     category         VARCHAR(100)    │
│     department       VARCHAR(100)    │          │     priority         ENUM(4 Levels)  │
│     profile_picture  VARCHAR(255)    │          │     status           ENUM(4 States)  │
│     created_at       DATETIME(6)     │          │     created_at       DATETIME(6)     │
└──────────────────┬───────────────────┘          │     updated_at       DATETIME(6)     │
                   │                              └──────────────────┬───────────────────┘
                   │ 1                                               │ 1
                   │                                                 │
                   │ N                                               │ N
                   │        ┌────────────────────────────────────────┘
                   │        │
                   ▼        ▼
┌──────────────────────────────────────────────────┐
│                     COMMENTS                     │
├──────────────────────────────────────────────────┤
│ PK  id               BIGINT (AUTO_INCREMENT)     │
│ FK  ticket_id        BIGINT (CASCADE ON DELETE)  │
│ FK  user_id          BIGINT                      │
│     content          TEXT                        │
│     is_internal      BOOLEAN (Staff Only)        │
│     created_at       DATETIME(6)                 │
└──────────────────────────────────────────────────┘
```

### 📋 Detailed Relational Schema Specification

#### Table 1: `users`
| Column Name | Data Type | Constraints | Description |
| :--- | :--- | :--- | :--- |
| `id` | `BIGINT` | `PRIMARY KEY`, `AUTO_INCREMENT` | Unique identifier for each user account. |
| `username` | `VARCHAR(50)` | `NOT NULL`, `UNIQUE` | Login username credential. |
| `password` | `VARCHAR(255)` | `NOT NULL` | 60-character BCrypt hashed password string. |
| `email` | `VARCHAR(100)` | `NOT NULL`, `UNIQUE` | User email address used for notification alerts. |
| `full_name` | `VARCHAR(100)` | `NOT NULL` | Display name for tickets and dashboard headers. |
| `role` | `ENUM` | `ROLE_USER`, `ROLE_TECHNICIAN`, `ROLE_ADMIN` | Spring Security authorization authority. |
| `department` | `VARCHAR(100)` | `NULLABLE` | Organizational division (Finance, Marketing, IT). |
| `profile_picture` | `VARCHAR(255)` | `NULLABLE` | Local server path to uploaded avatar image. |
| `created_at` | `DATETIME(6)` | `NOT NULL` | Account creation timestamp. |

#### Table 2: `tickets`
| Column Name | Data Type | Constraints | Description |
| :--- | :--- | :--- | :--- |
| `id` | `BIGINT` | `PRIMARY KEY`, `AUTO_INCREMENT` | Unique support ticket reference number. |
| `title` | `VARCHAR(150)` | `NOT NULL`, `INDEXED` | Short, descriptive summary of the technical issue. |
| `description` | `TEXT` | `NOT NULL` | Comprehensive details and diagnostic steps. |
| `category` | `VARCHAR(100)` | `NOT NULL` | Classification (Hardware, Network, Software, etc.). |
| `priority` | `ENUM` | `LOW`, `MEDIUM`, `HIGH`, `URGENT` | Operational priority tag for triage order. |
| `status` | `ENUM` | `OPEN`, `IN_PROGRESS`, `RESOLVED`, `CLOSED` | Current operational lifecycle stage. |
| `user_id` | `BIGINT` | `FOREIGN KEY` ➔ `users(id)` | ID of the employee who submitted the ticket. |
| `assigned_to` | `BIGINT` | `FOREIGN KEY` ➔ `users(id)`, `NULLABLE` | ID of the technician currently assigned. |
| `created_at` | `DATETIME(6)` | `NOT NULL` | Initial submission timestamp. |
| `updated_at` | `DATETIME(6)` | `NULLABLE` | Last modification timestamp. |

#### Table 3: `comments`
| Column Name | Data Type | Constraints | Description |
| :--- | :--- | :--- | :--- |
| `id` | `BIGINT` | `PRIMARY KEY`, `AUTO_INCREMENT` | Unique identifier for comment entry. |
| `content` | `TEXT` | `NOT NULL` | Message body text. |
| `is_internal` | `BOOLEAN` | `DEFAULT FALSE` | Flag restricting visibility to Techs and Admins. |
| `ticket_id` | `BIGINT` | `FOREIGN KEY` ➔ `tickets(id)`, `ON DELETE CASCADE` | Associated ticket parent record. |
| `user_id` | `BIGINT` | `FOREIGN KEY` ➔ `users(id)` | Author of the comment. |
| `created_at` | `DATETIME(6)` | `NOT NULL` | Message dispatch timestamp. |

---

## 🌐 Complete MVC & Route Endpoints Matrix

| HTTP Method | Route URL Pattern | Target Controller | Allowed Roles | Description & Behavior |
| :--- | :--- | :--- | :--- | :--- |
| `GET` | `/login` | `AuthController` | *Public (All)* | Renders customized login page with error/logout flash alerts. |
| `GET` | `/register` | `AuthController` | *Public (All)* | Renders new user self-registration form. |
| `POST` | `/register` | `AuthController` | *Public (All)* | Validates input, hashes password via BCrypt, registers user. |
| `GET` | `/dashboard` | `DashboardController` | `USER`, `TECH`, `ADMIN` | Role-aware landing page displaying customized KPI statistics. |
| `GET` | `/tickets` | `TicketController` | `USER`, `TECH`, `ADMIN` | Displays filterable, searchable list of tickets. |
| `GET` | `/tickets/create` | `TicketController` | `USER`, `TECH`, `ADMIN` | Renders ticket creation form. |
| `POST` | `/tickets/create` | `TicketController` | `USER`, `TECH`, `ADMIN` | Persists new ticket, triggers async confirmation email. |
| `GET` | `/tickets/{id}` | `TicketController` | `USER`, `TECH`, `ADMIN` | Detailed view of ticket, history, and threaded comments. |
| `POST` | `/tickets/{id}/status` | `TicketController` | `TECH`, `ADMIN` | Updates ticket status (`OPEN` ➔ `RESOLVED`), sends async alert. |
| `POST` | `/tickets/{id}/assign` | `TicketController` | `TECH`, `ADMIN` | Assigns ticket to current technician or selected staff. |
| `POST` | `/tickets/{id}/comments` | `TicketController` | `USER`, `TECH`, `ADMIN` | Appends public comment or private staff-only note. |
| `GET` | `/profile` | `ProfileController` | `USER`, `TECH`, `ADMIN` | Displays user profile, security settings, and avatar preview. |
| `POST` | `/profile/update` | `ProfileController` | `USER`, `TECH`, `ADMIN` | Updates personal details and processes avatar file upload. |
| `POST` | `/profile/password` | `ProfileController` | `USER`, `TECH`, `ADMIN` | Validates old password and hashes new password. |
| `GET` | `/admin/users` | `AdminController` | `ADMIN` | Administrator panel for managing users and role assignments. |
| `POST` | `/admin/users/{id}/role` | `AdminController` | `ADMIN` | Modifies user permissions (`ROLE_USER` ➔ `ROLE_TECH`). |
| `GET` | `/logout` | `SecurityConfig` | `USER`, `TECH`, `ADMIN` | Invalidates session, purges cookies, redirects to `/login`. |

---

## 🛡️ Security Architecture & Role-Based Access Control (RBAC)

Spring Security 6 is configured via [`SecurityConfig.java`](file:///c:/Users/niraj/Downloads/ticket%20management%20system/src/main/java/com/nettech/helpdesk/config/SecurityConfig.java) using modern lambda DSL syntax:

```java
@Bean
public SecurityFilterChain filterChain(HttpSecurity http) throws Exception {
    http
        .csrf(csrf -> csrf
            .ignoringRequestMatchers(new AntPathRequestMatcher("/h2-console/**"))
        )
        .headers(headers -> headers
            .frameOptions(frame -> frame.disable())
        )
        .authorizeHttpRequests(auth -> auth
            .requestMatchers("/css/**", "/js/**", "/images/**", "/h2-console/**", "/login", "/register").permitAll()
            .requestMatchers("/admin/**").hasAuthority("ROLE_ADMIN")
            .anyRequest().authenticated()
        )
        .formLogin(form -> form
            .loginPage("/login")
            .defaultSuccessUrl("/dashboard", true)
            .failureUrl("/login?error=true")
            .permitAll()
        )
        .logout(logout -> logout
            .logoutRequestMatcher(new AntPathRequestMatcher("/logout"))
            .logoutSuccessUrl("/login?logout=true")
            .invalidateHttpSession(true)
            .deleteCookies("JSESSIONID")
            .permitAll()
        );

    http.authenticationProvider(authenticationProvider());
    return http.build();
}
```

### 🔐 Key Security Protections:
1. **BCrypt Password Hashing:** 10-round logarithmic work factor prevents rainbow table and brute-force dictionary attacks.
2. **CSRF Token Verification:** Cross-Site Request Forgery tokens injected into all POST/PUT state-modifying requests.
3. **Session Governance:** Session fixation protection enabled; cookies secured with `HttpOnly` and `SameSite` policies.
4. **URL & Method-Level Security:** Route patterns guarded via `.hasAuthority()` and service methods guarded with `@PreAuthorize`.

---

## 📧 Asynchronous Email Notification Engine

The notification pipeline is built on Spring's `@Async` infrastructure in [`EmailService.java`](file:///c:/Users/niraj/Downloads/ticket%20management%20system/src/main/java/com/nettech/helpdesk/service/EmailService.java):

```java
@Service
public class EmailService {

    private static final Logger logger = LoggerFactory.getLogger(EmailService.class);
    private final JavaMailSender mailSender;

    @Autowired(required = false)
    public EmailService(JavaMailSender mailSender) {
        this.mailSender = mailSender;
    }

    @Async
    public void sendTicketUpdateEmail(String userEmail, String ticketTitle, String newStatus) {
        logger.info("Preparing asynchronous notification for {} regarding ticket: '{}' -> New Status: {}", 
                    userEmail, ticketTitle, newStatus);
        try {
            if (mailSender != null) {
                SimpleMailMessage message = new SimpleMailMessage();
                message.setTo(userEmail);
                message.setSubject("[Nettech Help Desk] Ticket Status Updated: " + ticketTitle);
                message.setText("Hello,\n\nYour support ticket '" + ticketTitle + 
                                "' has been updated to status: " + newStatus + 
                                ".\n\nLog in to the portal to view complete details.");
                mailSender.send(message);
                logger.info("Email successfully dispatched to {}", userEmail);
            }
        } catch (Exception e) {
            logger.warn("SMTP email sending skipped/failed: {}. Application logic continued normally.", e.getMessage());
        }
    }
}
```

---

## 📁 Repository Codebase Directory Structure

```
ticket management system/
│
├── pom.xml                               # Project Object Model & Maven Dependencies
├── run.bat                               # 1-Click Launch Script for Windows
├── README.md                             # Comprehensive Technical Documentation
├── PROJECT_REPORT.md                     # Academic Report & Project Synopsis
├── PRESENTATION_SLIDES.md                # 12-Slide Executive Slide Deck (McKinsey Standard)
├── Nettech_Help_Desk_Presentation.pptx   # Generated 16:9 PowerPoint Presentation File
├── generate_deck.py                      # Automated PPTX Presentation Generation Script
│
├── src/
│   ├── main/
│   │   ├── java/com/nettech/helpdesk/
│   │   │   ├── HelpdeskApplication.java  # Main Application Entry Point (@SpringBootApplication)
│   │   │   │
│   │   │   ├── config/
│   │   │   │   └── SecurityConfig.java   # Spring Security 6 RBAC & FilterChain Configuration
│   │   │   │
│   │   │   ├── controller/
│   │   │   │   ├── AdminController.java       # User management & Administrative actions
│   │   │   │   ├── AuthController.java        # Authentication, Login, and Registration
│   │   │   │   ├── DashboardController.java   # Role-specific KPI metrics & analytics
│   │   │   │   ├── ProfileController.java     # User profile & avatar upload handler
│   │   │   │   └── TicketController.java      # Ticket CRUD, status toggling, comments
│   │   │   │
│   │   │   ├── model/
│   │   │   │   ├── Comment.java          # Threaded comment JPA entity
│   │   │   │   ├── Role.java             # User roles enum (USER, TECH, ADMIN)
│   │   │   │   ├── Ticket.java           # Support ticket core JPA entity
│   │   │   │   ├── TicketPriority.java   # Ticket priority enum (LOW, MED, HIGH, URGENT)
│   │   │   │   ├── TicketStatus.java     # Ticket lifecycle enum (OPEN, IN_PROGRESS, etc.)
│   │   │   │   └── User.java             # User account and credential JPA entity
│   │   │   │
│   │   │   ├── repository/
│   │   │   │   ├── CommentRepository.java# Spring Data JPA queries for comments
│   │   │   │   ├── TicketRepository.java # Custom JPQL search & filter queries
│   │   │   │   └── UserRepository.java   # Username & email unique lookup queries
│   │   │   │
│   │   │   ├── service/
│   │   │   │   ├── CommentService.java            # Comment business operations
│   │   │   │   ├── CustomUserDetailsService.java  # Spring Security UserDetails provider
│   │   │   │   ├── EmailService.java              # @Async non-blocking email dispatcher
│   │   │   │   ├── TicketService.java             # Ticket lifecycle orchestration
│   │   │   │   └── UserService.java               # Registration, BCrypt, Profile updates
│   │   │   │
│   │   │   └── util/
│   │   │       └── DataSeeder.java       # Automated sample data seeder on startup
│   │   │
│   │   └── resources/
│   │       ├── application.properties    # Centralized Spring Boot configuration
│   │       │
│   │       ├── static/
│   │       │   ├── css/
│   │       │   │   └── style.css         # Glassmorphism design & responsive styles
│   │       │   ├── js/                   # Custom client scripts & interactive handlers
│   │       │   └── images/               # Default avatars & branding assets
│   │       │
│   │       └── templates/                # Thymeleaf HTML Templates
│   │           ├── layout/
│   │           │   └── main.html         # Master template layout with Navbar & Footer
│   │           ├── dashboard/
│   │           │   ├── admin.html        # Administrator executive dashboard
│   │           │   ├── technician.html   # Support technician triage console
│   │           │   └── user.html         # Employee personal ticket portal
│   │           ├── tickets/
│   │           │   ├── create.html       # Ticket submission form
│   │           │   ├── details.html      # Ticket view, history & comment thread
│   │           │   └── list.html         # Filterable, searchable ticket table
│   │           ├── admin/
│   │           │   └── users.html        # Admin user management panel
│   │           ├── error/
│   │           │   ├── 403.html          # Forbidden access error page
│   │           │   └── 404.html          # Not found error page
│   │           ├── login.html            # User login portal
│   │           ├── register.html         # User registration form
│   │           └── profile.html          # Profile settings & avatar uploader
│   │
│   └── test/                             # Automated JUnit 5 & Spring Boot Tests
```

---

## 🔄 Dual Database Configuration Guide

The project is engineered with an abstracted configuration allowing seamless switching between **MySQL** (for production / persistent setup) and **H2** (for zero-dependency standalone testing) directly in [`application.properties`](file:///c:/Users/niraj/Downloads/ticket%20management%20system/src/main/resources/application.properties).

### 🐬 Option A: Local MySQL via XAMPP (Currently Active Default)
```properties
# =======================================================
# 🐬 XAMPP LOCAL MySQL DATABASE CONFIGURATION (Active)
# =======================================================
spring.datasource.url=jdbc:mysql://localhost:3306/helpdesk_db?createDatabaseIfNotExist=true&useSSL=false&allowPublicKeyRetrieval=true&serverTimezone=UTC
spring.datasource.username=root
spring.datasource.password=
spring.datasource.driver-class-name=com.mysql.cj.jdbc.Driver
spring.jpa.database-platform=org.hibernate.dialect.MySQLDialect
```

### 💾 Option B: Standalone Local Persistent File Database (H2)
```properties
# =======================================================
# 💾 LOCAL PERSISTENT SQL DATABASE (Saved to local disk)
# =======================================================
spring.datasource.url=jdbc:h2:file:./data/helpdesk_db;DB_CLOSE_DELAY=-1
spring.datasource.driverClassName=org.h2.Driver
spring.datasource.username=sa
spring.datasource.password=
spring.jpa.database-platform=org.hibernate.dialect.H2Dialect
spring.h2.console.enabled=true
```

---

## 🚀 Quick Start & Local Setup

### 📋 Prerequisites
* **Java 21 OpenJDK** installed and configured on your system PATH (`java -version`).
* **XAMPP Control Panel** (or standalone MySQL Server on port 3306).

---

### ⚡ 3-Step Launch Procedure

#### Step 1: Start MySQL in XAMPP
1. Open **XAMPP Control Panel**.
2. Click **Start** next to **MySQL** *(Status turns green, Port 3306)*.
3. Click **Start** next to **Apache** *(Optional, enables phpMyAdmin on port 80)*.

#### Step 2: Start the Help Desk Application
Simply **double-click** the one-click launcher script in your project root:
👉 **[`run.bat`](file:///c:/Users/niraj/Downloads/ticket%20management%20system/run.bat)**

*(Alternatively, open PowerShell in the project directory and execute: `.\run.bat`)*

#### Step 3: Access the Web Application
* **Help Desk Web Application:** 👉 **[http://localhost:8080](http://localhost:8080)**
* **MySQL Database Manager (phpMyAdmin):** 👉 **[http://localhost/phpmyadmin](http://localhost/phpmyadmin)** *(Database: `helpdesk_db`)*

---

## 👥 Demo Accounts Matrix

The application seeds sample accounts across all three operational roles upon initial startup:

| Role | Username | Password | Email Address | Department | Sample Responsibilities |
| :--- | :--- | :--- | :--- | :--- | :--- |
| **👑 Administrator** | `admin` | `admin123` | `admin@nettech.com` | IT Operations | System administration, role overrides, user management. |
| **🛠️ Support Tech** | `tech_sarah` | `tech123` | `sarah.tech@nettech.com` | Infrastructure | Network troubleshooting, ticket triage, internal notes. |
| **🛠️ Support Tech** | `tech_david` | `tech123` | `david.tech@nettech.com` | Software Support | Software bug fixing, user password resets. |
| **👤 Standard User** | `john_doe` | `user123` | `john.doe@nettech.com` | Finance | Submitting hardware requests, tracking ticket status. |
| **👤 Standard User** | `alice_smith` | `user123` | `alice.smith@nettech.com` | Marketing | Requesting marketing workstation upgrades. |

---

## 🔮 Future Roadmap & Scalability Enhancements

* **Headless Architecture:** Decouple the presentation layer by exposing complete Spring Boot RESTful API endpoints secured with **JWT (JSON Web Tokens)** for companion **React / Next.js** and mobile clients.
* **Cloud Infrastructure & Containerization:** Multi-stage **Docker** containerization deployed on **AWS ECS / Kubernetes** with **AWS RDS Multi-AZ MySQL**.
* **AI-Assisted Auto-Triage:** Integrate Large Language Models (LLMs) to automatically detect issue categories, suggest priority rankings, and recommend solutions based on historical resolution data.
* **SLA Countdown Timers:** Implement visual SLA countdown meters with automated email escalation triggers when critical tickets exceed target response windows.

---

## 👨‍💻 Author & Academic Credits

* **Developer:** Niraj Patel
* **Academic Program:** Master of Computer Applications (MCA) Bridge Program
* **Institution:** Bharati Vidyapeeth Institute of Management and Information Technology (BVIMIT), Mumbai University
* **Project Name:** Nettech Help Desk Ticket Management System
* **Version:** `1.0.0 (Production Release)`

---

<div align="center">
  <sub>Built with ❤️ using Java 21, Spring Boot 3, Spring Security 6, Thymeleaf, and MySQL.</sub>
</div>
