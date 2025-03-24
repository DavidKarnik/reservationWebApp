# Reservation Web Application

On-line booking system mainly for conference rooms. The project focuses on visually appealing user experience, security and maintainability. The system allows users to browse available rooms, check equipment and capacity, and make reservations with real-time updates. Advanced authentication mechanisms, including 2FA, enhance security, while modern development practices ensure maintainability and efficiency.

## About

This is personal project for revise and learn more about whole application development. Aiming  on full-stack (frontend, backend, devops), system architecture, project roles and managment, sustainability, modern technologies and best practices. I want to deepen my knowledge of frontend development using React and Tailwind CSS. For the backend, I will use Spring Boot with Maven to build a robust, scalable and hopefully secure system. Also, I want to dive deeper into DevOps, including containerization, orchestration, automated deployment, and the usage of management and monitoring tools.

## Architecture

```bash
./
└── frontend/
    ├── aaa/
    │   └── aab
    └── bbb/
        ├── bbc.js
        └── bbd.css
└── backend/
    └── src/main
        ├── backend/
        └── resources/
├── .gitignore
└── README.md
```

## Used SW

## PostgreSQL Database

Open-source object-relational database system that offers high performance, scalability, and robust data management features. Almost too robust for my project, but I want to try this database and learn how it works. I used it also because of:

- Support for both relational and object-oriented data – efficiently handles complex data structures
- Transactional integrity (ACID-compliant) – atomicity, consistency, isolation, and durability
- Strong indexing support – enables fast searches
- JSON & JSONB support – for storing metadata about reservations
- Scalability – allows the application to grow without performance bottlenecks

So PostgreSQL should be fast, stable and secure.

## Database Structure  

### Rooms Table (Conference rooms)  

| Parameter   | Type         | Description                        |
|------------|-------------|--------------------------------------|
| `id`       | `BIGSERIAL`  | **Primary Key**. Unique room ID     |
| `name`     | `VARCHAR(255)` | Room name                         |
| `capacity` | `INT`        | Maximum number of people            |
| `equipment`| `TEXT[]`     | List of available equipment         |

### Reservations Table (Room reservations)  

| Parameter   | Type         | Description                           |
|------------|-------------|-----------------------------------------|
| `id`       | `BIGSERIAL`  | **Primary Key**. Unique reservation ID |
| `room_id`  | `BIGINT`     | **Foreign Key**. Linked to `rooms.id`  |
| `user_id`  | `BIGINT`     | **Foreign Key**. Linked to `users.id`  |
| `date`     | `DATE`       | Date of the reservation                |
| `start_time` | `TIME`     | Start time of the reservation          |
| `end_time` | `TIME`       | End time of the reservation            |
| `status`   | `VARCHAR(50)` | Reservation status (`pending`, `confirmed`, `canceled`) |

### Users Table (System users)  

| Parameter   | Type         | Description                          |
|------------|-------------|----------------------------------------|
| `id`       | `BIGSERIAL`  | **Primary Key**. Unique user ID       |
| `email`    | `VARCHAR(255) UNIQUE` | User email (login)           |
| `password` | `TEXT`       | Hashed password                       |
| `role`     | `VARCHAR(50)` | User role (`admin`, `user`)          |

- Future extensibility (e.g., notifications (when, how), pricing, AI recommendations)

## File Structure

